# Aviso legal · OsintCiberCrimeX

Última actualización: 2026-11-24

## 1. Naturaleza de la herramienta

OsintCiberCrimeX es un **buscador OSINT potenciado y específico** para crimen organizado y ciberamenazas. Construye un índice propio a partir de **fuentes públicas** (Wikidata, GDELT, MITRE ATT&CK, OFAC, ONU, OpenSanctions, URLhaus, Feodo, Ransomware.live, 46 feeds de ciberseguridad) y de **scraping pasivo** de canales públicos de Telegram (vista web `t.me/s/`).

**No** realiza escaneos activos, **no** explota vulnerabilidades, **no** contacta con infraestructura maliciosa y **no** envía tráfico a los indicadores que muestra.

El **scraping** es una **capacidad de ingesta**, no la identidad de la herramienta: el valor está en el índice y en la búsqueda especializada, no en raspar por raspar.

## 2. Fuentes

- Fuentes públicas citadas en el README.
- Canales **públicos** de Telegram (sin login, sin cuenta).
- **Sin verificación independiente.** Los datos reflejan lo que publican las fuentes, no una conclusión forense.

## 3. Uso permitido

- Investigación defensiva.
- Threat intelligence.
- Educación y docencia.
- Monitorización de amenazas en un SOC.
- Periodismo de investigación.

## 4. Uso prohibido

- Ataques activos, escaneos no autorizados o acceso a sistemas ajenos.
- Acciones legales basadas únicamente en estos datos.
- Acoso, doxxing o represalia contra personas u organizaciones.
- Vigilancia masiva de personas.
- Cualquier uso que infrinja la ley de tu jurisdicción o los términos de servicio de las fuentes.

## 5. Falsos positivos

La herramienta **puede equivocarse**. Los resultados son **coincidencias textuales automáticas** y **no implican vinculación ni responsabilidad**. Los grupos hacktivistas exageran y mienten; los canales se repiten entre sí; las IPs pueden ser víctimas, proxies, nodos Tor/VPN o IPs reasignadas.

**No tomes decisiones graves** (legales, laborales, de seguridad física o de represalia) basándote solo en lo que muestra esta herramienta. Contrasta siempre con la fuente original.

## 6. Privacidad y datos (RGPD)

- La herramienta **no** requiere cuenta de Telegram ni login.
- La herramienta **no** recopila datos personales de los usuarios de Telegram.
- Los mensajes leídos son **públicos**.
- Los resultados se guardan **localmente en tu máquina**. **Tú** eres el responsable del tratamiento bajo RGPD.
- Si eres titular de un canal y quieres que no se lea, **no lo listes** en `tg_channels.txt` o abre un issue.
- Si eres titular de una IP listada y crees que es un error, abre un issue y se revisa.

## 7. Terceros

- **Telegram**: el uso de `t.me/s/` está sujeto a los términos de Telegram. La herramienta solo hace lectura pasiva.
- **Dependencias**: las librerías de terceros tienen sus propias licencias (ver `requirements.txt`).
- **Nexus_Osint_X / Puente_Nexus / ThreatJarvisX**: herramientas del mismo ecosistema, con sus propios avisos legales.

## 8. Garantías

La herramienta se distribuye **«tal cual»**, sin garantías de ningún tipo, expresas o implícitas, incluyendo, pero no limitándose a, garantías de comerciabilidad, idoneidad para un propósito particular y no infracción. Ver `LICENSE` (AGPL-3.0).

## 9. Responsabilidad

El autor **no se responsabiliza** del uso indebido de la herramienta ni de las consecuencias derivadas de decisiones tomadas a partir de sus resultados. El uso es responsabilidad exclusiva de quien lo hace.

## 10. Licencia

AGPL-3.0. Ver [`LICENSE`](./LICENSE).

## 11. Contacto

Abre un issue en el repositorio para cualquier duda legal o de atribución. **No incluyas datos sensibles** en el issue.

Contacto comercial (servicios de inteligencia): **SpectrumSecIt@proton.me**.
