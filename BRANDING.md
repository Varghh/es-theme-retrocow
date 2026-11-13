# Identidad oficial

Maestro: `assets/branding/retrocow-master.png`, copia exacta del adjunto del usuario.
SHA256: `8f519bd31da3ecfb98faa2afd99ba406674dc3801f5c3cda22b91b2ae7df2492`.
Derivado: `assets/branding/retrocow-logo.png`, RGBA 1024×341, escalado proporcional por vecino más cercano; sin recoloración ni separación de elementos. El maestro mide 2172×724 y no se carga en el frontend.

Se conserva la relación de aspecto con PreserveAspectFit (Pegasus) y maxSize (EmulationStation). La marca queda fuera del carrusel en Pegasus y usa extra=static en el selector de EmulationStation. Ambos definen grilla 3×3. Las preferencias guardadas de Batocera pueden prevalecer sobre los valores del tema.

Validación de esta actualización: maestro idéntico byte por byte, PNG decodificables, XML analizado, revisión de rutas y diferencias, créditos/licencias preservados. La identidad no añade dependencias ni animaciones. El historial de validaciones anteriores no representa una ejecución de esta actualización. No se ejecutaron los frontends en esta revisión: queda pendiente comprobar visualmente 16:9 y 4:3, selección, lanzamiento y retorno en los dispositivos de destino. El ejecutable qmllint no está disponible en el entorno.
