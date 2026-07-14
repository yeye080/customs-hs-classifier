# Customs HS Code & Incoterms Logistics Simulator (v3.0)

Este es un simulador inteligente de logística internacional y despacho de aduanas desarrollado en **Python**. La herramienta clasifica automáticamente mercancías por búsqueda aproximada (*Fuzzy Matching*), calcula el cubicaje logístico, convierte divisas en tiempo real mediante API y determina la base imponible exacta de los impuestos aduaneros (Arancel e IVA) adaptándose a las reglas **Incoterms 2020**.

## Características Clave

*   **Motor de Búsqueda Aproximada (Fuzzy Matching):** Clasifica productos e identifica su código HS correspondiente, incluso si el usuario introduce términos con erratas o sinónimos coloquiales.
*   **Lógica Inteligente de Incoterms 2020 (EXW, FOB, CIF, DDP):** Reconstruye matemáticamente el valor de aduana (Valor CIF) sumando o deduciendo de forma automática los gastos de flete, seguro y aduana de exportación según la regla comercial seleccionada.
*   **Cálculo de Cubicaje y Peso Tasable:** Implementa los coeficientes estándar de la IATA (aéreo) y transporte marítimo/terrestre para calcular el volumen ($m^3$) y determinar si la naviera facturará por peso real o volumen ocupado.
*   **Conversor de Divisas en Tiempo Real:** Conectado a la API pública de *Open Exchange Rates* para procesar importaciones valoradas en USD, GBP o CNY y liquidar los impuestos en la moneda aduanera local (EUR).
*   **Semáforo de Riesgo en Despacho:** Alertas inmediatas basadas en el tipo de producto, indicando si requiere inspecciones fitosanitarias, licencias de importación médica, precintas especiales o controles de toxicidad infantil.
*   **Interfaz Gráfica Interactiva (GUI):** Diseñado con `ipywidgets` para permitir la modificación de variables en tiempo real en entornos como Google Colab, acompañado de gráficos dinámicos de desglose de costes con `matplotlib`.

## Tecnologías Utilizadas

*   **Python 3** como lenguaje principal.
*   **Pandas** para el modelado de la base de datos arancelaria sintética.
*   **Matplotlib** para la generación dinámica de gráficos de análisis de costes.
*   **IPywidgets** para la interfaz de usuario interactiva y formularios.
*   **Urllib & JSON** para la integración de APIs web externas en tiempo real.
   
## Ejemplo de Funcionamiento

Cuando un usuario simula la compra de un palet de café en origen por valor de **$10,000 USD** bajo condiciones **EXW**, el simulador:
1.  Obtiene el tipo de cambio USD/EUR en tiempo real.
2.  Suma los gastos de flete internacional, camión local y despacho de exportación para obtener la base imponible CIF.
3.  Calcula el peso volumétrico del palet para alertar sobre el peso tasable logístico.
4.  Liquida el arancel (7.5%) y el IVA de importación (10% acumulativo).
5.  Emite una **alerta roja de riesgo fitosanitario** por tratarse de materia prima agrícola.
6.  Dibuja un gráfico circular mostrando el porcentaje exacto que representan la mercancía, el transporte y los impuestos respecto al coste total puesto en almacén.
