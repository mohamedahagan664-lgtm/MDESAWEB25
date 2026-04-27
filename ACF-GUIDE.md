# Guía para Trabajar con ACF en WordPress

## Descripción General del Proyecto

El tema **Balinot** (Azure Meridian) es un tema de WordPress para una empresa de consultoría empresarial. Actualmente el proyecto:

- **Tipo**: Tema de WordPress personalizado
- **Ubicación**: `wp-content/themes/balinot`
- **Stack**: PHP, Tailwind CSS, WooCommerce
- **Estructura**: 
  - `functions.php` - Carga de archivos principales
  - `inc/setup.php` - Configuración del tema
  - `template-parts/sections/` - Secciones de la página (hero, expertise, why-choose, etc.)
  - `inc/woocommerce/` - Integración con WooCommerce

> **Nota**: El proyecto actualmente **NO utiliza ACF**. Todo el contenido está hardcodeado en los archivos PHP.

---

## ¿Qué es ACF?

**Advanced Custom Fields (ACF)** es un plugin de WordPress que permite crear campos personalizados (Custom Fields) de forma visual y administrarlos desde el panel de WordPress sin necesidad de programar.

### Ventajas de usar ACF:
- Interfaz visual en el admin de WordPress
- Tipos de campos variados (texto, imágenes, repetidores, etc.)
- Flexible y extensible
- Gran documentación y comunidad

---

## Instalación de ACF

### Opción 1: Plugin (Recomendado para principiantes)

1. Ve a **Plugins > Añadir nuevo**
2. Busca "Advanced Custom Fields"
3. Instala y activa el plugin gratuito (ACF)
4. Para campos avanzados, considera la versión PRO

### Opción 2: Incluir en el tema (Para desarrolladores)

```php
// En functions.php o archivo separado
if ( file_exists( get_theme_file_path( 'inc/acf.php' ) ) ) {
    require_once get_theme_file_path( 'inc/acf.php' );
}
```

---

## Estructura Recomendada para ACF en este Proyecto

### 1. Crear archivo de configuración ACF

Crea el archivo `inc/acf.php` en tu tema:

```php
// filepath: inc/acf.php
<?php
/**
 * ACF Configuration
 *
 * @package Balinot Theme
 */

if ( ! defined( 'ABSPATH' ) ) {
    exit;
}

// Registrar campos ACF programáticamente
function balinot_register_acf_fields() {
    if ( function_exists( 'acf_add_local_field_group' ) ) {
        
        // Grupo: Configuración de la página de inicio
        acf_add_local_field_group( array(
            'key' => 'group_homepage_settings',
            'title' => 'Configuración de Página de Inicio',
            'fields' => array(
                // Sección Hero
                array(
                    'key' => 'field_hero_title',
                    'label' => 'Título Principal',
                    'name' => 'hero_title',
                    'type' => 'text',
                ),
                array(
                    'key' => 'field_hero_subtitle',
                    'label' => 'Subtítulo',
                    'name' => 'hero_subtitle',
                    'type' => 'textarea',
                ),
                array(
                    'key' => 'field_hero_image',
                    'label' => 'Imagen de Fondo',
                    'name' => 'hero_image',
                    'type' => 'image',
                    'return_format' => 'url',
                ),
                array(
                    'key' => 'field_hero_cta_text',
                    'label' => 'Texto del Botón CTA',
                    'name' => 'hero_cta_text',
                    'type' => 'text',
                ),
                array(
                    'key' => 'field_hero_cta_link',
                    'label' => 'Enlace del Botón CTA',
                    'name' => 'hero_cta_link',
                    'type' => 'text',
                ),
                
                // Sección Expertise
                array(
                    'key' => 'field_expertise_title',
                    'label' => 'Título de Expertise',
                    'name' => 'expertise_title',
                    'type' => 'text',
                ),
                array(
                    'key' => 'field_expertise_cards',
                    'label' => 'Tarjetas de Expertise',
                    'name' => 'expertise_cards',
                    'type' => 'repeater',
                    'sub_fields' => array(
                        array(
                            'key' => 'field_card_icon',
                            'label' => 'Icono',
                            'name' => 'card_icon',
                            'type' => 'text',
                        ),
                        array(
                            'key' => 'field_card_title',
                            'label' => 'Título',
                            'name' => 'card_title',
                            'type' => 'text',
                        ),
                        array(
                            'key' => 'field_card_description',
                            'label' => 'Descripción',
                            'name' => 'card_description',
                            'type' => 'textarea',
                        ),
                    ),
                ),
                
                // Sección Why Choose Us
                array(
                    'key' => 'field_why_choose_title',
                    'label' => 'Título',
                    'name' => 'why_choose_title',
                    'type' => 'text',
                ),
                array(
                    'key' => 'field_why_choose_stats',
                    'label' => 'Estadísticas',
                    'name' => 'why_choose_stats',
                    'type' => 'repeater',
                    'sub_fields' => array(
                        array(
                            'key' => 'field_stat_number',
                            'label' => 'Número',
                            'name' => 'stat_number',
                            'type' => 'text',
                        ),
                        array(
                            'key' => 'field_stat_label',
                            'label' => 'Etiqueta',
                            'name' => 'stat_label',
                            'type' => 'text',
                        ),
                    ),
                ),
            ),
            'location' => array(
                array(
                    array(
                        'param' => 'page_type',
                        'operator' => '==',
                        'value' => 'front_page',
                    ),
                ),
            ),
        ));
        
        // Grupo: Opciones del tema
        acf_add_local_field_group( array(
            'key' => 'group_theme_options',
            'title' => 'Opciones del Tema',
            'fields' => array(
                array(
                    'key' => 'field_logo',
                    'label' => 'Logo',
                    'name' => 'theme_logo',
                    'type' => 'image',
                    'return_format' => 'url',
                ),
                array(
                    'key' => 'field_contact_email',
                    'label' => 'Email de Contacto',
                    'name' => 'contact_email',
                    'type' => 'email',
                ),
                array(
                    'key' => 'field_social_links',
                    'label' => 'Redes Sociales',
                    'name' => 'social_links',
                    'type' => 'repeater',
                    'sub_fields' => array(
                        array(
                            'key' => 'field_social_platform',
                            'label' => 'Plataforma',
                            'name' => 'platform',
                            'type' => 'select',
                            'choices' => array(
                                'linkedin' => 'LinkedIn',
                                'twitter' => 'Twitter',
                                'instagram' => 'Instagram',
                            ),
                        ),
                        array(
                            'key' => 'field_social_url',
                            'label' => 'URL',
                            'name' => 'url',
                            'type' => 'url',
                        ),
                    ),
                ),
            ),
            'location' => array(
                array(
                    'param' => 'options_page',
                    'operator' => '==',
                    'value' => 'acf-options',
                ),
            ),
        ));
    }
}
add_action( 'acf/init', 'balinot_register_acf_fields' );
```

### 2. Agregar página de opciones del tema

```php
// En functions.php o inc/acf.php
if ( function_exists( 'acf_add_options_page' ) ) {
    acf_add_options_page( array(
        'page_title'  => 'Opciones del Tema',
        'menu_title'  => 'Opciones del Tema',
        'menu_slug'   => 'acf-options',
        'capability'  => 'edit_posts',
        'redirect'    => false,
    ) );
}
```

---

## Cómo Usar los Campos ACF en las Plantillas

### Ejemplo: En `template-parts/sections/hero.php`

```php
<?php
// Obtener valores de ACF
$hero_title = get_field( 'hero_title' );
$hero_subtitle = get_field( 'hero_subtitle' );
$hero_image = get_field( 'hero_image' );
$hero_cta_text = get_field( 'hero_cta_text' );
$hero_cta_link = get_field( 'hero_cta_link' );

// Valores por defecto si no hay valores ACF
$hero_title = $hero_title ?: get_bloginfo( 'name' );
$hero_subtitle = $hero_subtitle ?: get_bloginfo( 'description' );
?>

<!-- En el HTML -->
<h1><?php echo esc_html( $hero_title ); ?></h1>
<p><?php echo esc_html( $hero_subtitle ); ?></p>
<?php if ( $hero_image ) : ?>
    <img src="<?php echo esc_url( $hero_image ); ?>" alt="">
<?php endif; ?>
<?php if ( $hero_cta_text ) : ?>
    <a href="<?php echo esc_url( $hero_cta_link ); ?>">
        <?php echo esc_html( $hero_cta_text ); ?>
    </a>
<?php endif; ?>
```

### Ejemplo: Con campos repetidor (Repeater)

```php
<?php
// Obtener el repetidor
$expertise_cards = get_field( 'expertise_cards' );

if ( $expertise_cards ) : ?>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <?php foreach ( $expertise_cards as $card ) : ?>
            <div class="card">
                <span class="material-symbols-outlined">
                    <?php echo esc_html( $card['card_icon'] ); ?>
                </span>
                <h4><?php echo esc_html( $card['card_title'] ); ?></h4>
                <p><?php echo esc_html( $card['card_description'] ); ?></p>
            </div>
        <?php endforeach; ?>
    </div>
<?php endif; ?>
```

---

## Tipos de Campos ACF Recomendados

| Tipo de Campo | Uso en este proyecto | Ejemplo |
|---------------|---------------------|---------|
| `text` | Títulos, etiquetas | Título del hero |
| `textarea` | Descripciones largas | Subtítulo |
| `image` | Fotos, logos | Imagen de fondo |
| `url` | Enlaces externos | Links de CTA |
| `email` | Contacto | Email de contacto |
| `repeater` | Listas dinámicas | Tarjetas de servicios, estadísticas |
| `select` | Opciones fijas | Tipo de página |
| `wysiwyg` | Contenido rico | Descripciones largas |
| `color_picker` | Colores | Colores de marca |
| `file` | Documentos PDF | Descargables |

---

## Mejores Prácticas

### 1. Usar nombres de campo descriptivos
```php
// ✅ Bueno
'hero_title', 'expertise_cards', 'contact_email'

// ❌ Evitar
'field_1', 'title', 'my_field'
```

### 2. Siempre sanitizar la salida
```php
// ✅ Usar funciones de escape
echo esc_html( get_field( 'text_field' ) );
echo esc_url( get_field( 'url_field' ) );
echo wp_kses_post( get_field( 'html_field' ) );

// ✅ Para imágenes
$image = get_field( 'hero_image' );
if ( $image ) {
    echo '<img src="' . esc_url( $image['url'] ) . '" alt="' . esc_attr( $image['alt'] ) . '">';
}
```

### 3. Proporcionar valores por defecto
```php
$title = get_field( 'hero_title' );
if ( ! $title ) {
    $title = 'Valor por defecto';
}
```

### 4. Verificar si ACF está instalado
```php
// Verificar antes de usar
if ( function_exists( 'get_field' ) ) {
    $value = get_field( 'my_field' );
}
```

### 5. Organizar grupos de campos lógicamente
- **Página de Inicio**: Campos específicos del front-page
- **Opciones del Tema**: Configuración global
- **SEO**: Metadatos personalizados
- **Footer**: Información del pie de página

---

## Estructura de Archivos Recomendada

```
balinot/
├── functions.php              # Cargar ACF
├── inc/
│   ├── acf.php                # Definición de campos
│   ├── acf-json/              # Guardar campos como JSON
│   │   └── group_xxx.json
│   └── template-tags.php      # Funciones helper para ACF
└── template-parts/
    └── sections/
        ├── hero.php           # Usar get_field('hero_title')
        ├── expertise.php      # Usar get_field('expertise_cards')
        └── why-choose.php     # Usar get_field('why_choose_stats')
```

---

## Recursos Adicionales

- **Documentación oficial**: https://www.advancedcustomfields.com/resources/
- **ACF PRO**: https://www.advancedcustomfields.com/pro/
- **Campos disponibles**: https://www.advancedcustomfields.com/resources/#field-types

---

## Próximos Pasos para Implementar en Balinot

1. **Instalar el plugin ACF** en el sitio de WordPress
2. **Crear el archivo `inc/acf.php`** con la configuración de campos
3. **Modificar las plantillas** de `template-parts/sections/` para usar `get_field()`
4. **Crear una página de opciones** para configuración global del tema
5. **Probar** que los campos se guarden y muestren correctamente

---

*Documento generado para el tema Balinot - Abril 2026*