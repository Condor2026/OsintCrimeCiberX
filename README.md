# 🔎 OsintCiberCrimeX · Buscador OSINT potenciado de crimen y cyber

**Buscador especializado en crimen organizado y ciberamenazas.** No es un agregador de feeds ni un simple scraper: es un **motor de búsqueda** con índice propio, lógica de consulta específica y capacidad de scraping para alimentarse.

[![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)]()
[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Version](https://img.shields.io/badge/version-1.15.0-green.svg)]()
[![OSINT](https://img.shields.io/badge/OSINT-crime%20%2B%20cyber-00D4FF)]()
[![Search](https://img.shields.io/badge/search-specialized-8B5CF6)]()

> ⚠️ **Aviso legal**: herramienta de investigación. Los resultados son coincidencias textuales automáticas y **no implican vinculación ni responsabilidad**. Verifica siempre en la fuente original. Ver [LEGAL.md](LEGAL.md).

![TheCondor](image(1).jpg)

---

## 🇬🇧 English summary

A **specialized OSINT search engine** (Python 3.8+) for **organized crime** and **cyber threat intelligence**. Unlike feed aggregators or plain scrapers, it maintains its own index, applies domain-specific query logic and classification (Andrómeda-style, with health 🏥 / energy ⚡ threat detection), and uses **passive scraping** (public Telegram channels, 15+ public sources) as one of its ingestion capabilities. Self-hosted web panel with world map, charts, translation and persistent history. **Free and open source under AGPL-3.0.** See [LEGAL.md](LEGAL.md) for GDPR notes.

---

## 🧩 Ecosistema Nexus · cada herramienta en su casa

OsintCiberCrimeX forma parte del ecosistema **Nexus**, un conjunto de herramientas independientes que se comunican por APIs HTTP locales. Cada una vive en su propio repositorio y se puede usar por separado.

| Herramienta | Rol | Repositorio | Estado |
|---|---|---|---|
| **Nexus_Osint_X** | **Radar / base de mando OSINT**: agrega eventos, correlaciona, mapa 3D, ATT&CK, panel JARVIS | `Condor2026/Nexus_Osint_X` | Prototipo funcional (v3.1) |
| **OsintCiberCrimeX** (este repo) | **Buscador potenciado y específico** de crimen y cyber: índice propio + scraping pasivo + búsqueda especializada | `Condor2026/OsintCiberCrimeX` | **v1.15.0** funcional · release ampliada **dic 2026** |
| **ThreatJarvisX** | Asistente IA que consulta Nexus por su API | repositorio propio | Activo |
| **Puente_Nexus** | Enlace OsintCiberCrimeX ↔ Nexus: lanza, vigila y sincroniza IOCs | `Condor2026/Nexus_Osint_X` | v1.1 funcional |

**Diferencia clave entre Nexus y OsintCiberCrimeX:**

- **Nexus** es un **radar**: observa lo que pasa, agrega eventos de 330+ fuentes, correlaciona, dibuja en el mapa. No busca por ti; te muestra el panorama.
- **OsintCiberCrimeX** es un **buscador**: tú preguntas por un grupo, una IP, un CVE, un canal o un patrón, y él busca en su índice especializado. El scraping es **cómo se alimenta**, no lo que es.

```
┌───────────────────┐        ┌──────────────────┐        ┌─────────────────┐
│ OsintCiberCrimeX  │  IOCs  │  Puente_Nexus    │ watch  │  Nexus_Osint_X  │
│   (buscador)      │ ─────► │  (repo Nexus)    │ ─────► │  (radar/mando)  │
└───────────────────┘        └──────────────────┘        └─────────────────┘
                                                                  ▲
                                                                  │ API HTTP
                                                           ┌──────┴───────┐
                                                           │ ThreatJarvisX │
                                                           │  (asistente)  │
                                                           └───────────────┘
```

> **Este repo solo contiene OsintCiberCrimeX.** Nexus_Osint_X, ThreatJarvisX y el Puente_Nexus viven en sus propios repositorios. La integración se detalla en [Integración con Nexus](#-integración-con-nexus-puente_nexus).

---

## 🧭 ¿Qué es esto?

OsintCiberCrimeX es un **buscador OSINT potenciado y específico** para **crimen organizado** y **ciberamenazas**. A diferencia de un agregador de feeds (que muestra lo que va llegando) o de un scraper suelto (que extrae sin más), OsintCiberCrimeX:

1. **Construye y mantiene su propio índice** a partir de fuentes públicas y scraping pasivo.
2. **Aplica lógica de consulta específica** del dominio: alias de grupos, variantes de nombres, expansión de términos, scoring de relevancia.
3. **Clasifica** los resultados con reglas estilo Andrómeda (tipo de ataque, salud 🏥, energía ⚡, IOCs).
4. **Enlaza siempre a la fuente original** para que el analista verifique.

### Qué busca

- **Crimen organizado**: cárteles, maras, mafias, grupos terroristas, guerrillas.
- **Ciberamenazas**: APTs, ransomware, botnets, DDoS, hacktivismo, campañas.
- **Entidades**: grupos, personas buscadas, organizaciones sancionadas, canales.
- **IOCs**: IPs, dominios, CVE, hashes, hashtags, países.
- **Mensajes**: de canales públicos de Telegram, con metadatos e historia.

### Qué lo hace «potenciado»

- **Diccionario de crackers** (~600 grupos) que **expande** la búsqueda con variantes (`LockBit` = `Lock Bit` = `LockBit3`) y **puntúa** los resultados. No filtra: puntúa.
- **Deduplicación** por URL y por nombre normalizado.
- **Clasificación Andrómeda**: tipo de ataque + sector crítico (salud, energía) + IOCs extraídos.
- **Historia de grupos**: primera/última aparición, actividad por mes, mapa de calor, co-menciones, picos.
- **Scraping pasivo** de canales públicos de Telegram (`t.me/s/`) y 15+ fuentes públicas: el índice se mantiene fresco sin intervención.

### Qué lo hace «específico»

- **Dos modos** (crime / cyber) con fuentes, entidades y colores distintos.
- **Búsqueda por entidad, grupo, canal, IOC, texto y patrón**.
- **Panel web** con mapa mundial, gráficos, historial y traducción.
- **Exportes** pensados para análisis: dossier HTML, GraphML (Gephi/Cytoscape), JSON, CSV, API.

### Para qué sirve (y para qué no)

✅ **Sirve para**:
- Buscar información pública dispersa sobre un grupo concreto.
- Detectar amenazas a **sectores críticos** (salud, energía) en mensajes de Telegram.
- Generar **dossiers HTML** con fuentes verificables.
- Monitorizar la actividad de grupos hacktivistas conocidos.
- Alimentar una base de datos local con IOCs (IPs, dominios, CVE, hashtags).
- Cruzar lo que encuentra con un radar como Nexus (vía Puente_Nexus).

❌ **No sirve para**:
- Atribuir delitos (una coincidencia textual no es una prueba).
- Vigilancia masiva de personas.
- Sustituir a un analista humano.
- Sustituir a las fuentes originales (siempre enlaza a ellas).
- Ser un radar pasivo: para eso está Nexus.

---

## ✨ Características

### 🔍 Buscador especializado
- **15+ fuentes integradas** y **scraping pasivo** de canales públicos de Telegram.
- **Índice propio** (SQLite local) con deduplicación y normalización.
- **Diccionario de crackers** (~600 grupos) que expande la consulta con variantes y **puntúa** los resultados.
- **Búsqueda por entidad, grupo, canal, IOC, texto y patrón**.

### 🧠 Clasificación estilo Andrómeda
- Detección automática de **tipo de ataque**: DDoS, botnet, ransomware, malware, phishing, exploit, filtración…
- **Amenazas a la salud** 🏥 y a la **energía** ⚡ mediante listas de palabras clave en español, inglés, ruso y árabe.
- **IOCs extraídos** de los mensajes: IPs, dominios, CVE, hashtags, países.

### 📡 Scraping pasivo (capacidad de ingesta)
- Lectura **pasiva** de canales **públicos** (`t.me/s/<canal>`). Sin cuenta, sin unirse, sin escribir.
- **Metadatos** del canal: ID interno, fecha de creación, renombres, contadores, verificado.
- **Historia de grupos**: primera/última aparición, actividad por mes, mapa de calor día×hora, co-menciones, picos.
- **Descubrimiento pasivo** por nombre cuando no tienes el canal.
- **Escáner en segundo plano** con barra de progreso, ETA y botón de parada.
- Respeta límites: caché de 1 h, un solo hilo por URL, backoff exponencial, pausa automática si Telegram responde 429.

### 🗺️ Panel web
- **Mapa mundial** interactivo (zoom, arrastrar, filtro, exportar SVG).
- **Gráficos** de actividad, tipos, fuentes, grupos, canales.
- **Historial persistente** con snapshots (puedes abrir búsquedas antiguas sin volver a consultar fuentes).
- **Traducción** de evidencias a ES/EN/PT (Google Translate + MyMemory como respaldo).
- **Modo ahorro** para equipos modestos (sin animaciones ni desenfoques).

### 📤 Exportes
- **Dossier HTML** por entidad (con fuentes enlazadas).
- **GraphML** de co-ocurrencias (abrible en Gephi / Cytoscape).
- **JSON** completo de la base.
- **CSV** de mensajes de Telegram.
- **API JSON** (`/api/mensajes`) compatible con la estructura de eventos de Andrómeda.

---

## 🚀 Instalación rápida

### Requisitos
- **Python 3.8+** (probado en 3.10–3.12).
- **Nada más** es obligatorio: la herramienta usa solo la librería estándar.

### Dependencias opcionales (recomendadas)
Mejoran el scraper de Telegram y la velocidad:

```bash
pip install -r requirements.txt
```

Si no las tienes, la herramienta funciona igual (con `urllib` y un parser propio).

### Clonar y ejecutar

```bash
git clone https://github.com/Condor2026/OsintCiberCrimeX
cd OsintCiberCrimeX
python OsintCiberCrimeX.py
```

Para el panel web:

```bash
python OsintCiberCrimeX.py --web --port 8765
```

Abre `http://127.0.0.1:8765` en el navegador.

---

## 🎯 Uso rápido

### Terminal

```bash
# Buscar en modo crimen (por defecto)
python OsintCiberCrimeX.py --buscar "Cartel de Sinaloa"

# Buscar en modo cyber
python OsintCiberCrimeX.py --buscar "LockBit" --mode cyber

# Ver ficha de una entidad
python OsintCiberCrimeX.py --report 42

# Generar dossier HTML
python OsintCiberCrimeX.py --dossier 42 dossier_lockbit.html

# Ver mensajes de Telegram (estilo Andrómeda)
python OsintCiberCrimeX.py --feed --feed-group KillNet --feed-limit 30

# Estadísticas de los mensajes
python OsintCiberCrimeX.py --feed-stats

# Historia de un grupo
python OsintCiberCrimeX.py --group KillNet

# Exportar base completa a JSON
python OsintCiberCrimeX.py --export dump.json

# Exportar grafo de co-ocurrencias
python OsintCiberCrimeX.py --export-graph grafo.graphml
```

### Panel web

```bash
python OsintCiberCrimeX.py --web --port 8765
```

Rutas principales:
- `/` — buscador y estadísticas
- `/historial` — memoria de búsquedas
- `/telegram` — panel único: escáner, fichas de grupo, gráficos, mensajes, canales
- `/e/<id>` — ficha de entidad
- `/dossier/<id>` — dossier HTML descargable
- `/api/mensajes` — API JSON de mensajes clasificados

### Scraping de Telegram

1. Crea un archivo `tg_channels.txt` con un canal público por línea (sin `@`, sin `https://`).
2. Impórtalos:

```bash
python OsintCiberCrimeX.py --tg-import
```

3. Escanea (modo pasivo, respeta límites automáticamente):

```bash
python OsintCiberCrimeX.py --tg-update --tg-pages 0 --tg-workers 0
```

> Las invitaciones privadas (`t.me/+hash`) **no se pueden leer** con este método. Solo canales públicos.

---

## 🔗 Integración con Nexus (Puente_Nexus)

El **Puente_Nexus** (incluido en el repo de **Nexus_Osint_X**) conecta este buscador con el radar **Nexus_Osint_X**. Funciona como un proceso aparte: lanza/vigila ambas, sincroniza IOCs y cruza eventos. **No modifica** ni este repo ni Nexus.

### Qué necesita del lado de OsintCiberCrimeX

Según el puente v1.1, se consumen estos endpoints:

| Método | Ruta | Para qué |
|---|---|---|
| `GET` | `/api/escaner` | Healthcheck / estado del escáner |
| `GET` | `/api/iocs?c2=1` | IOCs marcados como C2 |
| `GET` | `/api/iocs?ioc_tipo=ip` | IOCs de tipo IP |
| `GET` | `/api/iocs?ioc_tipo=cve` | IOCs de tipo CVE |

> ⚠️ La versión actual (`v1.15.0`) expone `/api/mensajes`. Los endpoints `/api/escaner` y `/api/iocs` están **previstos para la release ampliada de diciembre 2026** para compatibilidad total con el puente. Hasta entonces, la sincronización automática OsintCiberCrimeX → Nexus quedará limitada a lo que el puente pueda leer. La herramienta funciona igual sin el puente.

### Cómo arrancar el ecosistema completo

Con `OsintCiberCrimeX.py`, `Nexus_Osint_X.py` y `Puente_Nexus.py` en la misma carpeta:

```bash
python Puente_Nexus.py --all
# → lanza OsintCiberCrimeX (8765) + Nexus (8000) + panel del puente (8800)
# → sincroniza IOCs a la watchlist de Nexus cuando la API esté disponible
```

Ver el repo de **Nexus_Osint_X** para más detalles del puente.

### Contacto para servicios

El autor ofrece servicios de inteligencia sobre esta base (informes CTI, monitorización, dossiers, formación, tooling a medida). Contacto comercial: **SpectrumSecIt@proton.me**.

---

## 📚 Fuentes integradas

| Fuente | Modo | Tipo | Actualización |
|---|---|---|---|
| [Wikidata](https://www.wikidata.org/) | Crime + Cyber | Entidades | En vivo |
| [Wikipedia](https://www.wikipedia.org/) | Crime + Cyber | Prensa | En vivo |
| [GDELT](https://www.gdeltproject.org/) | Crime + Cyber | Noticias | En vivo |
| [Google News](https://news.google.com/) | Crime + Cyber | Noticias | En vivo |
| [FBI Wanted](https://www.fbi.gov/wanted) | Crime | Personas buscadas | En vivo |
| [INTERPOL](https://www.interpol.int/) | Crime | Notificaciones rojas | En vivo |
| [ONU (Consolidated)](https://scsanctions.un.org/) | Crime | Sanciones | Bajo demanda |
| [OFAC SDN](https://sanctionssearch.ofac.treas.gov/) | Crime | Sanciones | Bajo demanda |
| [OpenSanctions](https://www.opensanctions.org/) | Crime | Sanciones | Bajo demanda |
| [RSS oficiales](https://www.justice.gov/) | Crime | Prensa | En vivo |
| [Ransomware.live](https://www.ransomware.live/) | Cyber | Víctimas | En vivo |
| [Ransomwatch](https://github.com/joshhighet/ransomwatch) | Cyber | Archivo (2020–2025) | Congelada |
| [RansomLook](https://www.ransomlook.io/) | Cyber | Grupos | En vivo |
| [CISA KEV](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) | Cyber | Vulnerabilidades | En vivo |
| [URLhaus](https://urlhaus.abuse.ch/) | Cyber | URLs maliciosas | En vivo |
| [Feodo Tracker](https://feodotracker.abuse.ch/) | Cyber | IPs C2 | En vivo |
| [MITRE ATT&CK](https://attack.mitre.org/) | Cyber | Grupos, malware, campañas | En vivo |
| 46 feeds de ciberseguridad | Cyber | Prensa | En vivo |
| **Telegram** (pasivo) | Cyber | Mensajes de canales públicos | Local |

Todas las fuentes son públicas y de acceso libre. Cada resultado enlaza a su **URL original**.

---

## 🏗️ Cómo funciona

```
consulta → expansión de variantes → índice propio (SQLite) + 15+ fuentes en paralelo
         → deduplicación → clasificación → búsqueda especializada
         → terminal / panel web / dossier / GraphML / JSON / API
```

**Filosofía del proyecto**:
1. **Nunca inventar datos**: si una fuente falla, se avisa; no se rellena con "probables".
2. **Nunca descartar por score**: el diccionario de crackers **puntúa**, no filtra.
3. **Enlazar siempre a la fuente original**: cada evidencia tiene su URL.
4. **Respetar los servidores**: caché de 1 h, un solo hilo por URL, backoff exponencial, pausa automática si Telegram responde 429.
5. **El scraping es una capacidad, no la identidad**: el valor está en el índice y en la búsqueda especializada, no en raspar por raspar.

---

## 🧪 Modo Crimen vs Modo Cyber

| | **Crime** | **Cyber** |
|---|---|---|
| **Fuentes** | Wikidata, Wikipedia, GDELT, Google News, FBI, INTERPOL, ONU, OFAC, OpenSanctions, RSS oficiales | Wikidata, Wikipedia, GDELT, Google News, Ransomware.live, RansomLook, CISA KEV, URLhaus, Feodo, MITRE, 46 feeds, Telegram |
| **Entidades típicas** | Cárteles, maras, mafias, terroristas, guerrillas | APTs, ransomware, botnets, hacktivistas, campañas |
| **Colores por tipo** | Azul (crime) | Violeta (grupos), rojo (ransomware), naranja (malware), cian (botnets), amarillo (DDoS), verde (campañas) |
| **Clasificación Andrómeda** | — | ✅ Sí (salud, energía, tipo de ataque) |
| **Telegram pasivo** | — | ✅ Sí |

Cambia de modo con `--mode crime|cyber` o desde el botón del panel web.

---

## 🧠 Diccionario de crackers

El archivo `cracker_dict.txt` contiene ~600 nombres de grupos, APTs, ransomware y hacktivistas. Se usa para:
1. **Expandir** la búsqueda con variantes (`DarkStormTeam` → `Dark Storm Team`, `dark_storm_team`…).
2. **Puntuar** los resultados (los que coinciden suben al principio; los que no, quedan neutros, no se descartan).

```bash
python OsintCiberCrimeX.py --dict-stats
python OsintCiberCrimeX.py --dict-test KillNet
```

---

## 📄 Exportes

```bash
python OsintCiberCrimeX.py --dossier 42 dossier.html
python OsintCiberCrimeX.py --export-graph grafo.graphml
python OsintCiberCrimeX.py --export dump.json
python OsintCiberCrimeX.py --history-export historial.json
```

---

## 📁 Estructura del repo

```
.
├── OsintCiberCrimeX.py         # Aplicación completa (v1.15.0)
├── tg_channels.txt             # Lista de canales públicos (una por línea)
├── cracker_dict.txt            # Diccionario de ~600 grupos/APTs/ransomware
├── requirements.txt            # Dependencias opcionales
├── .env.example                # Variables de configuración (opcional)
├── .gitignore
├── LICENSE
├── README.md
├── CHANGELOG.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
├── LEGAL.md
├── ACCESSIBILITY.md
├── .github/
│   └── PULL_REQUEST_TEMPLATE.md
└── image(1).jpg                # Imagen de cabecera
```

Archivos que se crean en runtime (no versionados): base de datos local, cachés, historial, logs. Ver `.gitignore`.

---

## ⚖️ Legal y privacidad

Esta herramienta **no aloja ni recopila datos personales por sí misma**. Es un buscador que consulta fuentes públicas y guarda los resultados **localmente en tu máquina**. Si la ejecutas, **tú** eres el responsable del tratamiento bajo RGPD.

👉 **Lee [LEGAL.md](LEGAL.md)** antes de usarla con datos de personas.

---

## 🤝 Contribuir

Lee [CONTRIBUTING.md](CONTRIBUTING.md) para:
- Añadir fuentes nuevas.
- Reportar bugs de scraping.
- Mejorar la clasificación.
- Traducir la interfaz.

Antes de abrir un PR, asegúrate de no commitear archivos con datos personales (`.db`, `.jsonl`, `.xml`). Están en `.gitignore`.

---

## 🔒 Seguridad

Si encuentras una vulnerabilidad, **no abras un issue público**. Lee [SECURITY.md](SECURITY.md).

---

## 💼 Servicios

El autor ofrece servicios de inteligencia sobre esta base:

- **Informes CTI a medida** (KillNet, LockBit, APT28… con MITRE ATT&CK e IOCs).
- **Monitorización continua** con alertas.
- **Dossiers** personalizados por grupo o sector.
- **Formación** en OSINT.
- **Desarrollo de tooling a medida**.

📬 **Contacto comercial**: SpectrumSecIt@proton.me

---

## 📜 Licencia

**GNU Affero General Public License v3.0 (AGPL-3.0)**. Ver [LICENSE](LICENSE).

- ✅ Puedes usar, copiar, modificar y distribuir el código.
- ✅ Puedes usarlo comercialmente.
- ⚠️ Si lo modificas y lo distribuyes (o lo ofreces como servicio en red), **debes publicar tus cambios bajo la misma licencia**.
- ⚠️ No hay garantía.

Si necesitas una **licencia comercial sin las obligaciones de AGPL**, contacta con el autor.

---

## 🙏 Agradecimientos

- A la comunidad OSINT por mantener las fuentes públicas que hacen posible este proyecto.
- A todos los que reportéis bugs y añadáis fuentes.

---

**Hecho con 🛡️ por un analista, para analistas.**
