# Autoevaluación de criterios

Esta tabla describe **implementación**, no ejecución de pruebas. Los estados «implementado» indican que la lógica o estructura está presente, pero no equivalen a pruebas aprobadas.

| Caso | Estado | Observación |
|---|---|---|
| CP-PF22-01 | No se pudo implementar | No hay capturas reales adjuntas ni publicación HTTPS. |
| CP-PF22-02 | Implementado | La lógica usa la misma variable APK_URL para enlace y QR; QR se oculta sin enlace. Prueba de redirección publicada pendiente. |
| CP-PF22-03 | No se pudo implementar | Ambas páginas existen y muestran metas, pero faltan los borradores aprobados. |
| CP-PF23-01 | No se pudo implementar | Los seis tipos están implementados en el cliente, pero se necesita clave pública y verificar fecha/estado en Supabase. |
| CP-PF23-02 | Implementado | La validación impide enviar sin consentimiento. No se ha hecho prueba de navegador. |
| CP-PF23-03 | Implementado | Se comprueba límite de 1000 caracteres después de trim; caso de 1001 definido en código. |
| CP-PF23-04 | Implementado | Validación de formato rechaza correo@; caso definido en código. |
| CP-PNF07-02 | No se pudo implementar | Se incorporan controles de accesibilidad, pero no se ha auditado contraste ≥4,5:1 ni teclado completo. |
| CP-PS09-01 | Implementado | Privacidad y eliminación de cuenta tienen enlaces locales; página de privacidad es borrador. |
| CP-PS10-01 | No se pudo implementar | Depende de políticas RLS en Supabase no accesibles desde esta entrega. |
| CP-PS11-01 | Implementado | El honeypot omite POST y muestra éxito según código; no se ha probado en navegador. |
