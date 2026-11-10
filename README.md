# Recibo Claro

Software de **liquidación de sueldos y recibos** para empresas uruguayas. Lo usa RR.HH. o el contador para calcular el sueldo de cada empleado, emitir los recibos y saber cuánto se paga al BPS y cuánto le cuesta cada empleado a la empresa.

> Proyecto del desafío **"El Artefacto de Software Empresarial (Back-End)"**. Introducción a la Tecnología y Cultura Digital · Licenciatura en Negocios Digitales · Universidad ORT Uruguay · 2026.

## Qué hace

| Sección | Qué hace |
|---|---|
| **Panel** | Líquido a pagar, nominal, lo que se paga al BPS, costo total para la empresa, costo por empleado, pasos del mes y controles. |
| **Empleados** | Ficha de cada empleado: mensual o jornalero, sueldo o jornal, categoría del Consejo de Salarios, mail, cónyuge e hijos a cargo (FONASA e IRPF), Fondo de Solidaridad, pensión alimenticia y retenciones (cuota sindical, préstamos, alquiler…). Calcula antigüedad y días de licencia. |
| **Novedades del mes** | Dos pestañas. *Sueldo:* faltas, días trabajados, horas extra, nocturnidad, feriados, comisiones, alimentación, adelantos y otros descuentos. *Ausencias:* licencia, certificación médica, accidente de trabajo, seguro de paro y licencias especiales (estudio, paternidad, matrimonio, duelo, hijo con discapacidad, donación de sangre o PAP, familiar a cargo). **Con IA:** se escriben en texto libre ("Martín hizo 6 horas extra y Valentina faltó el lunes") y la IA las carga en la planilla, mostrando los cambios antes de aplicarlos. |
| **Liquidación** | Calcula todos los recibos del mes. Controles automáticos (sueldo bajo el mínimo, horas extra sobre el límite, líquido negativo, cambios bruscos) y **revisión con IA**. Se cierra y emite los recibos. Exporta la planilla a Excel (CSV) y la **nómina para BPS** (resumen por empleado para pasar a GAFI). |
| **Recibos** | Recibo con datos de la empresa (RUT, BPS, MTSS), haberes, descuentos, líquido, aportes patronales y firmas. Descargar, imprimir o **preparar el mail** para el empleado (texto listo y botón para abrir el correo). **Con IA:** explica el recibo en lenguaje simple y arma un mensaje para mandarle al empleado. |
| **Aguinaldo** | 1/12 de lo cobrado en el semestre (diciembre a mayo → junio; junio a noviembre → diciembre), con sus descuentos. Proyección y emisión de recibos. |
| **Egresos** | Liquidación final por despido (común o especial), renuncia, mutuo acuerdo o fin de contrato: días trabajados, licencia no gozada, salario vacacional, aguinaldo proporcional e indemnización. |
| **Locación** | Elegís el país de la empresa (Uruguay, Argentina, Chile, Paraguay o Brasil) y muestra sus reglas de sueldo fundamentales: mínimo, jornada, aportes, impuesto a la renta, aguinaldo, vacaciones y despido, con fuentes y una tabla comparativa. El cálculo automático de recibos es de Uruguay. |
| **Empresa y parámetros** | Datos de la empresa, valores legales editables, **categorías y laudos** del Consejo de Salarios y aumento por ronda (sube laudos y sueldos). Respaldo y restauración de datos. Empresa de ejemplo. |

## Cálculos (valores 2026)

- **BPC:** $ 6.864 · **Salario mínimo nacional:** $ 25.383 (desde el 1/7/2026).
- **Aportes personales:** jubilatorio 15% (con tope), FONASA 3% a 8% según ingreso (2,5 BPC) y cónyuge o hijos a cargo, FRL 0,1%.
- **Aportes patronales:** jubilatorio 7,5%, FONASA 5%, FRL 0,1%, FGCL 0,025% y BSE según rubro.
- **IRPF:** franjas de 7, 10, 15, 30, 50, 75 y 115 BPC (0% a 36%). Base +6% si supera 10 BPC. Deducciones (aportes y 20 BPC anuales por hijo) al 14% hasta 15 BPC y al 8% por encima. Aguinaldo y salario vacacional a la tasa marginal.
- **Horas extra:** valor hora = jornal ÷ (horas semanales ÷ 6); +100% en días hábiles y +150% en descanso o feriado. **Nocturnidad:** +20% del valor hora.
- **Licencia:** 20 días; desde el 5.º año, 1 día más cada 4 años. **Salario vacacional:** jornal líquido × días de licencia, sin aportes.
- **Indemnización por despido (mensuales):** 1 mes por año o fracción, máximo 6, con incidencia de aguinaldo y salario vacacional; exenta de aportes e IRPF. Jornaleros: 2 jornales cada 25 días trabajados, máximo 150.

- **Certificación médica, accidente y seguro de paro:** esos días no los paga la empresa. El recibo estima el subsidio: enfermedad 70% desde el 4.º día (tope $ 67.754); seguro de paro 50% del promedio de 6 meses (mínimo $ 8.467, tope $ 67.754) o 12 jornales.
- **Licencias especiales pagas:** estudio 6, 9 o 12 días al año según horas (con 6 meses de antigüedad), paternidad, matrimonio y duelo 3 días, hijo con discapacidad 10 días al año, familiar a cargo 64 horas pagas al año, donación de sangre o PAP 1 día. A los mensuales no les cambia el sueldo; a los jornaleros se les pagan.
- **Alimentación:** sin aportes hasta 100 UI por día trabajado y el 20% del sueldo; el excedente aporta. Paga IRPF entera (DGI).
- **Fondo de Solidaridad:** $ 286 a $ 1.621 por mes según categoría; se deduce del IRPF.
- **Pensión alimenticia y retenciones (Ley 17.829):** la pensión va primero; después alquiler, sindicato, BROU, vivienda, seguro de vida, mutual, préstamos y convenios, en ese orden. El trabajador cobra al menos el 35% de su nominal menos aportes e IRPF (30% para alquiler y préstamos); lo que no entra se recorta y se avisa.
- **Ajuste anual de IRPF (diciembre):** escala anual sobre las rentas del año sin el 6%, deducciones al 14% u 8% (180 BPC), aguinaldo y vacacional a la tasa máxima, menos lo ya retenido. Si da a favor del trabajador no se retiene y lo resuelve DGI; lo retenido en diciembre no pasa del 20% de la renta del mes.
- **Despidos especiales:** enfermedad, doble; accidente de trabajo o denuncia al BPS, triple; embarazo, acoso sexual o discapacidad, común + 6 sueldos (150 jornales).
- **Laudos:** control de que nadie cobre menos que el mínimo de su categoría.

Fuentes: BPS Comunicado R 5/2026 (BPC, escala de IRPF y Fondo de Solidaridad), BPS Comunicado de ajuste anual de IRPF, BPS tasas FONASA y subsidios, MTSS (salario mínimo), leyes 16.713, 17.829, 18.345 y DGI (alimentación). Los valores se pueden cambiar en **Empresa y parámetros**. El tope jubilatorio y la tasa del BSE conviene confirmarlos con BPS y BSE.

## Archivos

| Archivo | Qué es |
|---|---|
| `index.html` | La página completa. |
| `server.js` | Servidor para Render: sirve la página y conecta la IA (Google Gemini, plan gratis) con la clave guardada en Render. Sin dependencias. |
| `package.json` | Datos del proyecto para Node. |
| `README.md` | Este archivo. |

**Dónde quedan los datos:** en Render, en el navegador de la computadora de quien usa la página (por eso hay **Descargar respaldo** y **Restaurar respaldo**). Dentro de Claude, en la base de datos de la página.

## Publicarlo en Render

1. **GitHub:** creá un repositorio nuevo, público, por ejemplo `recibo-claro`. Tocá **uploading an existing file**, subí los 4 archivos y tocá **Commit changes**.
2. **Render:** **+ New → Web Service** → elegí el repositorio → **Connect**.
   - **Language:** Node
   - **Build Command:** `npm install`
   - **Start Command:** `node server.js`
   - **Instance Type:** Free
3. **Environment Variables:** `GEMINI_API_KEY` = tu clave de Google AI Studio (la misma que usás en Cazador de Tendencias sirve).
4. **Deploy Web Service.** Cuando diga **Live**, abrí el link. Abajo a la izquierda tiene que decir **IA lista (Gemini)**.
5. La primera vez tocá **Cargar empresa de ejemplo** para probar con 7 empleados, o cargá tu empresa en **Empresa y parámetros**.

Con el plan gratis, si nadie entra en 15 minutos el servidor se duerme y la siguiente visita tarda cerca de 1 minuto.

## Limitaciones

- Es un **MVP** para mostrar el proceso: no reemplaza a un contador ni a los programas homologados para presentar ante BPS y DGI.
- Los laudos no vienen cargados: hay que copiarlos del decreto del Consejo de Salarios de cada grupo. Los del ejemplo son inventados.
- La nómina para BPS es un resumen: no es el archivo oficial de ATYR/GAFI.
- Los subsidios del BPS se muestran como estimación; los calcula y paga el BPS.
- El mail se abre con el texto listo, pero el recibo hay que adjuntarlo a mano.
- No incluye primas por antigüedad ni el tope conjunto del 20% con salud, seguros y transporte (solo alimentación).
- La licencia no gozada se liquida sin aportes, según el criterio publicado por datosUruguay; algunos contadores la gravan. Confirmalo con tu contador.
- En el plan gratis de Gemini, Google puede usar los pedidos para mejorar sus productos: los nombres de los empleados de ejemplo son inventados.
