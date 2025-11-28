============================
Website Product Visibility
============================

Este módulo permite controlar la visibilidad de productos, categorías y marcas de productos para diferentes tipos de usuarios en un sitio web de Odoo. Ofrece un sistema completo de filtrado personalizado para empresas que necesitan restringir el acceso a ciertos productos según los roles de usuario o configuraciones específicas.

Características Principales
==========================

Control de Visibilidad Dual
---------------------------

Soporta dos tipos de usuarios con configuraciones independientes:

* **Usuarios Invitados**: Visitantes anónimos del sitio web
* **Usuarios Registrados**: Clientes con configuraciones de visibilidad individuales

Modos de Filtrado
-----------------

La aplicación soporta 8 modos de filtrado diferentes:

**Para Usuarios Registrados:**

* **Sin Filtro**: Muestra todos los productos
* **Por Producto**: Oculta productos específicos
* **Por Categoría**: Oculta categorías de productos completas
* **Por Marca de Producto**: Oculta marcas específicas
* **Por Producto y Categoría**: Oculta productos y categorías específicas
* **Por Producto y Marca**: Oculta productos y marcas específicas
* **Por Categoría y Marca**: Oculta categorías y marcas específicas
* **Por Producto, Categoría y Marca**: Filtrado completo con los tres tipos

**Para Usuarios Invitados:**

Los mismos modos de filtrado pero configurados globalmente a través de la configuración del sistema.

Funcionalidades Clave
====================

Control a Nivel de Producto
----------------------------

* Oculta productos específicos de la visibilidad del sitio web
* Solo los productos publicados (`is_published = True`) pueden ser filtrados
* Mantiene las relaciones y categorizaciones existentes de productos

Gestión de Categorías
--------------------

* Oculta categorías completas de productos y sus subcategorías
* Herencia automática hacia categorías hijas
* Utiliza el modelo `product.public.category` para categorías del sitio web

Filtrado por Marcas
------------------

* Oculta marcas de productos específicas (requiere el módulo `product_brand`)
* Se integra con el sistema de gestión de marcas de Odoo
* Soporta filtrado de productos basado en marcas

Implementación Técnica
======================

Modelos Extendidos
------------------

* **res.partner**: Campos de visibilidad y modo de filtrado para clientes
* **product.template**: Búsqueda extendida para incluir filtrado de visibilidad
* **product.public.category**: Búsqueda extendida para filtrado por categorías
* **res.config.settings**: Configuración global para usuarios invitados

Controladores
------------

* Extiende `website_sale.controllers.main.WebsiteSale`
* Sobrescribe `_get_search_domain()` para incluir reglas de visibilidad
* Maneja lógica para usuarios invitados y registrados
* Utiliza expresiones de dominio para filtrar productos dinámicamente

Integración de UI
----------------

* Formulario de partner incluye pestaña "Product Visibility"
* Configuración del sistema incluye configuración global
* Widgets de botones de radio para selección de modo de filtrado
* Widgets de etiquetas many2many para seleccionar elementos a ocultar

Casos de Uso
============

* **E-commerce B2B**: Mostrar diferentes catálogos de productos a diferentes segmentos de clientes
* **Restricciones Regionales**: Ocultar productos no disponibles en ciertas regiones
* **Precios por Niveles**: Ocultar productos premium del público general
* **Control de Inventario**: Ocultar productos sin stock de grupos específicos de usuarios
* **Gestión de Marcas**: Controlar qué marcas son visibles para diferentes tipos de clientes

Instalación
============

1. Copie el módulo en el directorio de addons de Odoo
2. Reinicie el servidor Odoo
3. Vaya a Aplicaciones y busque "Website Product Visibility"
4. Instale el módulo

Dependencias
============

* `contacts`: Para gestión de clientes
* `website_sale`: Para funcionalidad e-commerce
* `product_brand`: Para capacidades de filtrado por marcas

Configuración
============

Para Usuarios Registrados
-------------------------

1. Venta → Clientes
2. Seleccione un cliente
3. Vaya a la pestaña "Product Visibility"
4. Configure el modo de filtrado deseado
5. Seleccione los productos, categorías o marcas a ocultar

Para Usuarios Invitados
-----------------------

1. Vaya a Configuración → Ajustes → General
2. Busque la sección "Website Product Visibility"
3. Configure el modo de filtrado para usuarios invitados
4. Seleccione los productos, categorías o marcas a ocultar

Licencia y Mantenimiento
========================

Esta aplicación es mantenida y actualizada para Odoo 15.

Para soporte y más información, visite la documentación oficial de Odoo.