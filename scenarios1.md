# 1: Simulación de Escaneo de Seguridad

```
FUNCTION authenticateUser(username, password):
  QUERY database WITH username AND password
  IF found RETURN True
  ELSE RETURN False
```


  

## __Vulnerabilidades__ 

* Inyección SQL: Si veo que el código toma entrada de usuario sin filtrarla y la usa directamente en una consulta, hay un riesgo de SQL Injection.
* XSS (Cross-Site Scripting): Si se muestran entradas de usuario en la interfaz sin procesarlas bien, podría ser un punto de ataque.
* CSRF (Cross-Site Request Forgery): Si el sistema usa sesiones abiertas, tengo que asegurarme de que nadie pueda aprovecharlas para ejecutar acciones en nombre del usuario.
## __Soluciones__
* Aplicaría consultas parametrizadas y sanitización de entrada en los puntos críticos para evitar inyecciones SQL.

* Validación de entrada en el cliente y el servidor: esto evita que el usuario envíe datos maliciosos.
* Content Security Policy (CSP) en el front-end para bloquear scripts no autorizados y prevenir XSS.
