# Trabajo Práctico Integrador

**Del problema al deploy: una app con un modelo de IA, publicada y defendida**

Seminario de Actualización · Tecnicatura Superior en Ciencia de Datos e IA · IFTS N.º 18
Docente: Cynthia M. Villagra · Ciclo lectivo 2026 · Segundo cuatrimestre

**Modalidad**: individual (opcional en grupo) · **Entrega**: viernes 09/10/2026, en la clase presencial

---

## Qué tenés que hacer

Elegí un **problema concreto y chico** que se pueda resolver con un modelo de IA ya entrenado
(lo que hicimos en clase: inferir, no entrenar). Armá una app que lo resuelva, **publicala en
internet** y defendé cada decisión técnica que tomaste.

**El deploy lo hacés como quieras**: Render, Streamlit Community Cloud, Hugging Face Spaces (si tu
cuenta lo permite), Railway, PythonAnywhere u otra plataforma. Gradio o Streamlit, `pipeline` o
`InferenceClient`. **No hay una respuesta correcta. Lo que se evalúa es que sepas explicar por qué
elegiste lo que elegiste y por qué no otra cosa.**

Ejemplos de problemas, solo para inspirarte (podés inventar el tuyo):

- clasificar reseñas de un comercio en positivas, neutras o negativas;
- ordenar consultas de clientes por tipo (problema técnico, facturación, reclamo) con *zero-shot*;
- detectar la emoción de un mensaje antes de contestarlo;
- cualquier otra tarea del Hub: resumir, traducir, completar texto, describir una imagen.

---

## Requisitos mínimos

1. **La app está online y funciona**: alguien que no sos vos abre el link, escribe algo y recibe
   una respuesta del modelo.
2. **El TP va en una carpeta nueva de tu repo general** (el portfolio de la cursada), por ejemplo
   `TP_Integrador/`, con: `app.py` (o equivalente), `requirements.txt`, un `README.md` que alguien
   pueda seguir sin preguntarte nada, y un historial de commits que muestre el progreso (no un
   solo commit al final).

---

## Qué entregás (los tres archivos son obligatorios)

### 1. Notebook (`.ipynb`)

La notebook es tu **laboratorio**: muestra cómo llegaste a la decisión. Tiene que incluir:

- **Comparación de al menos dos modelos candidatos** para tu problema, con las mismas frases de
  prueba (mínimo 8 frases, y al menos 2 que estén pensadas para que el modelo se equivoque:
  ironía, otro idioma, jerga, texto muy corto).
- Una **tabla de resultados** (frase, etiqueta, puntaje, ¿acertó?) por modelo.
- **El mismo llamado hecho de las dos formas**: con `pipeline` (el modelo corre en tu compu o en
  Colab) y con `InferenceClient` (corre en los servidores de Hugging Face). Medí y anotá **cuánto
  tarda** cada una.
- **Lectura del valor de retorno**: mostrá con `type()` qué devuelve cada forma y cómo accedés al
  resultado (diccionario o atributo).
- Celdas de texto que expliquen qué vas viendo. Una notebook sin explicaciones no se aprueba.

### 2. Informe (`.pdf`, 4 a 8 páginas)

Respondé **con tus palabras** y apoyándote en lo que muestra tu notebook. Usá los títulos tal cual:

**A. El problema**
1. ¿Qué problema querés resolver y para quién? ¿Por qué un modelo de IA y no unas reglas
   escritas a mano (un `if` con palabras clave)?

**B. El modelo**
2. ¿Qué modelos consideraste y por qué te quedaste con uno? Citá lo que leíste en su **model
   card**: tarea, etiquetas, idiomas, datos de entrenamiento, tamaño de los pesos.
3. ¿Dónde se equivoca? Mostrá ejemplos reales de tu notebook y explicá **por qué creés** que se
   equivoca, relacionándolo con los datos con los que fue entrenado.
4. Tu app, ¿está **entrenando** o **infiriendo**? Explicá la diferencia con tu propio caso.

**C. Dónde corre cada cosa**
5. **¿Dónde vive el código y dónde vive el modelo?** Hacé un esquema simple (cajas y flechas, a
   mano o en cualquier herramienta) con los lugares que intervienen en tu app: tu compu, GitHub,
   la plataforma de deploy y Hugging Face. En cada caja anotá qué hay ahí, y marcá con flechas qué
   viaja de un lugar a otro cuando alguien usa la app. Tiene que quedar claro: ¿dónde está guardado
   tu código? ¿Dónde se ejecuta? ¿Dónde están los pesos del modelo y dónde se hace la inferencia?
6. ¿Usaste `pipeline` o `InferenceClient` en la app publicada? Justificalo con números (memoria del
   plan gratuito, peso del modelo, tiempo de respuesta). ¿Qué pasaría si hubieras elegido la otra?

**D. El deploy**
7. ¿Dónde deployaste y por qué ahí? Compará tu elección con **al menos otras dos** opciones vistas
   en clase (hosting compartido, VPS, PaaS, serverless, nubes elásticas) y explicá por qué las
   descartaste. ¿Por qué tu app necesita un servidor que quede encendido?

**E. Lo que se rompió**
8. **Documentá al menos dos errores reales** que te aparecieron durante el trabajo. Para cada uno:
   - el **mensaje de error** completo (captura o texto copiado);
   - **dónde apareció**: en tu compu, en la plataforma de deploy o en Hugging Face;
   - **qué lo causaba**;
   - **cómo lo resolviste**, paso a paso, como para que otra persona pueda seguirlo.
9. **Límites de tu solución**: ¿qué pasa si la usan 1000 personas a la vez? ¿Si Hugging Face cambia
    las condiciones del plan gratuito (como ya pasó con los Spaces)? ¿Qué cambiarías para que sea
    un producto real?

**F. Vocabulario**
10. Tomá **5 líneas de tu `app.py`** y señalá en ellas: una clase, una instancia, un método, un
    atributo, un parámetro y su argumento, y un valor de retorno.

Al final: **link a la app**, **link a la carpeta del TP en tu repo** y, si usaste IA generativa para ayudarte, **para qué
la usaste** (está permitido; no declararlo, no).

### 3. Presentación (`.pptx`, 6 a 10 diapositivas)

Pensala para contársela en **5 minutos** a alguien que tiene que decidir si usa tu app. Tiene que
tener, como mínimo:

- el problema, en una diapositiva;
- el modelo elegido y por qué;
- dónde vive el código y dónde vive el modelo;
- la decisión de deploy y la alternativa que descartaste;
- una captura de la app funcionando y el link;
- un error que te enseñó algo;
- los límites y el próximo paso.

Poco texto, una idea por diapositiva. **Se presenta en la clase presencial del 09/10.**

---

## Cómo se evalúa

| Criterio | Peso |
|---|---|
| App online y funcionando | 20 % |
| Notebook: comparación de modelos, pruebas, `pipeline` vs. `InferenceClient` | 20 % |
| **Justificación de las decisiones técnicas** (modelo, dónde corre, plataforma) | 30 % |
| Uso correcto de los conceptos de clase (inferir, API, dónde vive cada cosa, tipos de hosting, vocabulario) | 15 % |
| Carpeta del TP y README reproducibles, historial de commits | 10 % |
| Presentación clara | 5 % |

**Condición para aprobar**: la app tiene que estar online al momento de la corrección, y el
informe tiene que responder todas las preguntas. Una respuesta del tipo "lo hice así porque así se
hizo en clase" **no cuenta como justificación**.

---

## Formato de entrega

En el aula virtual, en la tarea "TP Integrador", subí:

- `TP_Apellido_Nombre.pdf`
- `TP_Apellido_Nombre.ipynb`
- `TP_Apellido_Nombre.pptx`

Subilos antes de la clase del **viernes 09/10/2026** y pegá en el texto de la entrega el **link de
la app** y el **link a la carpeta del TP en tu repo general**. Ese día se presenta en forma presencial. Si es en grupo, entrega
una sola persona y en el informe y la presentación figuran todos los integrantes.

---

## Ayudas

- Todo lo que necesitás ya lo vimos: Clases 4 (Gradio), 5 (deploy y criterios de hosting) y 6
  (inferencia, model card, `InferenceClient`), más la notebook *pipeline vs. InferenceClient*:
  `github.com/cynthiavillagra/hugging_face_models`.
- **Empezá por el deploy de una app mínima**, aunque sea un "Hola". Cuando eso funcione, sumá el
  modelo. Lo que más tiempo lleva es lo que se rompe al publicar.
