# 2: Diseño de Autenticación JWT


```
DEFINE FUNCTION generateJWT(userCredentials):
  IF validateCredentials(userCredentials):
    SET tokenExpiration = currentTime + 3600 // Token expires in one hour
    RETURN encrypt(userCredentials + tokenExpiration, secretKey)
  ELSE:
    RETURN error
```

## Creación del Token:

* Usaría una clave fuerte o un esquema de claves pública/privada

* Me enfocaría en claims mínimos, incluyendo solo lo necesario en el token (por ejemplo, ID de usuario, roles, expiración) para evitar exponer datos sensibles.

* Limitaría el tiempo de vida del token y configuraría un sistema de renovación cada cierto tiempo para reducir los riesgos si el token es robado.
## Control de Expiración y Renovación:

* Tiempo de expiración corto: Ajustaría el tiempo de vida del token a entre 15 minutos y 1 hora, según las necesidades de la aplicación. Usaría un refresh token para renovar la sesión sin que el usuario tenga que volver a autenticarse.

* Implementaría una lista de revocación o gestionaría una versión de usuario en la base de datos para invalidar tokens cuando sea necesario (ej. si el usuario cambia de contraseña).

## Validación en Cada Solicitud:

* Verificación de firma en cada solicitud para asegurarme de que el token no ha sido manipulado y que sigue vigente.

* Usaría validación de IP o dispositivo si el token incluye estos datos, reduciendo el riesgo si alguien intenta reutilizar un token en un dispositivo distinto.