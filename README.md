# Custom Category Template + JSON-LD + Price for ocStore / OpenCart
## Module for Custom Product Page Templates with JSON-LD Microdata and Price Enhancements
[![License](https://img.shields.io/badge/license-BSD-blue.svg)](https://github.com/webitproff/oc-custom_category_template_jsonld_price/blob/main/LICENSE)
[![Version](https://img.shields.io/badge/version-1.5-green.svg)](https://github.com/webitproff/oc-custom_category_template_jsonld_price/releases)
[![ocStore Compatibility](https://img.shields.io/badge/ocStore-3.0.3.7-orange.svg)](https://ocstore.com/)
[![PHP](https://img.shields.io/badge/PHP-7.3-blueviolet.svg)](https://www.php.net/releases/7_3_0.php)

## Overview

<img src="https://raw.githubusercontent.com/webitproff/oc-custom_category_template_jsonld_price/refs/heads/main/Opencart-Custom-Product-Page-Templates-2025-1.webp" alt="Custom Product Page Templates for Category for ocStore / OpenCart">

### 👀 [View in the marketplace](https://abuyfile.com/en/market/opencart/oc-mods/custom-product-page-templates-for-category-on-ocstore-opencart)

**Custom Category Template + JSON-LD + Price** is a free OCMOD-based module for ocStore/OpenCart that enhances product pages by:
1. Assigning custom templates to products based on their category.
2. Adding JSON-LD microdata for improved SEO.
3. Including price and currency information for structured data.
4. Indicating out-of-stock status.

This module modifies the product page controller (`catalog/controller/product/product.php`) to dynamically select templates for specific product categories and enrich product pages with JSON-LD structured data for search engine optimization. It has been tested with **ocStore 3.0.3.7 + PHP 7.3** but may work with other OpenCart 3.x versions (test on a site copy first).

## Introduction for Beginners
The **Custom Category Template + JSON-LD + Price** module customizes how product pages are displayed in your ocStore/OpenCart online store. It allows you to use different templates for products in specific categories (e.g., a unique template for "Generators") and adds structured data (JSON-LD) to improve how search engines like Google understand your product pages. It also includes price and stock information for better SEO and user experience.

**Why is this needed?**
- **Custom Templates**: Products in different categories (e.g., Generators, E-bikes, or Scooters) may need unique layouts or designs. This module lets you assign specific templates to products based on their category.
- **SEO Enhancement**: JSON-LD microdata helps search engines display rich snippets (e.g., product name, price, and availability) in search results, improving visibility.
- **Price and Stock**: Adds price (including special prices) and stock status to the product page data, making it easier to display or use in templates.

**Important for beginners**: Always back up your website (files and database) before installing any module. Use tools like FileZilla for files and phpMyAdmin for the database to ensure you can restore your site if needed.

### Why It Matters
- **Better User Experience**: Custom templates allow tailored designs for different product types, improving how customers interact with your store.
- **SEO Benefits**: JSON-LD microdata can improve search engine rankings and click-through rates by providing structured information about products.
- **Flexibility**: Easily extendable for additional categories or templates without major code changes.

## Key Features
- Dynamically assigns custom templates to products based on their category ID.
- Adds JSON-LD microdata for product name, description, price, and currency.
- Handles special prices (discounts) and falls back to regular prices when no special price is available.
- Indicates out-of-stock status for products with zero or negative quantity.
- Processes product descriptions to remove HTML tags and convert `<br>` tags to spaces for clean JSON-LD output.
- Uses OCMOD for seamless integration without overwriting core files.
- Supports UTF-8 encoding for multilingual compatibility.
- Lightweight and focused, modifying only the product page controller.

## Module File Structure
This module is an OCMOD XML file that modifies the `catalog/controller/product/product.php` file. No additional files are included in the module itself, but it references custom template files that must exist in the `catalog/view/theme/your_theme/template/product/` directory.

```
catalog/
├── controller/
│   └── product/
│       └── product.php # Modified by OCMOD to add custom template logic and JSON-LD
├── view/
│   └── theme/
│       └── your_theme/
│           └── template/
│               └── product/
│                   ├── product.twig # Default product template
│                   └── product_generator.twig # Example custom template for category ID 468
```

## Requirements
Ensure your store meets these requirements:
- **ocStore/OpenCart**: Version 3.0.3.7 (other OpenCart 3.x versions may work, but test on a site copy).
- **PHP**: Version 7.3. Check in the admin panel: "System" → "Server Info" → "PHP Version."
- **File Access**: Requires FTP (via FileZilla) or hosting panel access (cPanel, DirectAdmin, etc.) to upload the OCMOD file and custom templates.
- **Custom Templates**: Custom template files (e.g., `product_generator.twig`) must exist in your theme’s template directory.
- **Database**: MySQL or MariaDB, accessible via phpMyAdmin for backups.
- **Theme**: Your store must use a theme that supports Twig templates.

**How to check PHP version?**
1. Log into the admin panel.
2. Go to "System" → "Server Info."
3. Find "PHP Version." If it’s not 7.3, contact your hosting provider to update.

## Detailed Installation Instructions
Follow these steps to install the module, designed for beginners and advanced users alike.

### 1. Downloading the Module
- Visit the project page on GitHub: [https://github.com/webitproff/oc-custom_category_template_jsonld_price](https://github.com/webitproff/oc-custom_category_template_jsonld_price).
- Click "Code" → "Download ZIP" and extract the archive, or download the OCMOD XML file directly.
- Advanced users can clone the repository: `git clone https://github.com/webitproff/oc-custom_category_template_jsonld_price.git`.

### 2. Preparing Custom Templates
- Ensure custom template files (e.g., `product_generator.twig`) exist in your theme’s template directory: `catalog/view/theme/your_theme/template/product/`.
- Example: For category ID 468, create `product_generator.twig` based on your default `product.twig` template, customizing it as needed.
- If custom templates are missing, the module will fall back to the default `product/product.twig`.

### 3. Uploading the OCMOD File
- Log into your ocStore/OpenCart admin panel.
- Navigate to **Extensions → Installer**.
- Click **Upload** and select the OCMOD XML file (e.g., `custom_category_template_jsonld_price.ocmod.xml`).
- Wait for the upload to complete successfully.

### 4. Installing the Module
- Go to **Extensions → Modifications**.
- Locate "Custom Category Template + JSON-LD + Price" in the list.
- Click the **Refresh** button (circular arrows) to apply the OCMOD changes.
- Verify that the modification is enabled (green checkmark).

### 5. Clearing Cache
- Go to **System → Tools → Cache Manager** (or equivalent in your admin panel).
- Clear both the system cache and template cache to ensure the changes take effect.

### 6. Verifying Installation
- Open a product page belonging to a category with a custom template (e.g., category ID 468).
- Check the page source (right-click → "View Page Source") for JSON-LD microdata in a `<script type="application/ld+json">` tag.
- Ensure the correct template is loaded (e.g., `product_generator.twig` for category ID 468).

## Using the Module
### 1. Custom Template Assignment
- The module checks the categories of a product using `$this->model_catalog_product->getCategories($product_id)`.
- It uses a predefined array to map category IDs to custom templates:
  ```php
  $custom_templates = [
      468 => 'product/product_generator',
      // 455 => 'product/product_ebike',
      // 785 => 'product/product_escooter'
  ];
  ```
- If a product belongs to a category listed in `$custom_templates`, the module uses the specified template (e.g., `product/product_generator` for category ID 468). Otherwise, it falls back to `product/product`.
- To add more custom templates, edit the `$custom_templates` array in the OCMOD XML file, uncommenting or adding new entries for other category IDs and their corresponding templates.

### 2. JSON-LD Microdata
- The module adds the following data to the product page for JSON-LD:
  - **Product Name**: `$data['oct_micro_heading_title']` and its JSON-encoded version `$data['oct_micro_heading_title_json']`.
  - **Description**: `$data['oct_description_microdata']` (HTML-decoded) and `$data['oct_description_microdata_json']` (stripped of HTML tags, with `<br>` tags replaced by spaces).
  - **Price**: `$data['oct_price_microdata']` (uses special price if available, otherwise regular price, cast to float).
  - **Currency**: `$data['oct_price_currency']` (defaults to 'UAH' if no currency is set in the session).
  - **Stock Status**: `$data['out_of_stock']` (true if product quantity is ≤ 0).
- These variables are available in your Twig template for rendering JSON-LD structured data.

### 3. Customizing Templates
- In your custom template (e.g., `product_generator.twig`), you can access the new variables:
  - `{{ oct_micro_heading_title }}`: Product name.
  - `{{ oct_description_microdata }}`: Full description (HTML).
  - `{{ oct_micro_heading_title_json }}`: JSON-encoded product name.
  - `{{ oct_description_microdata_json }}`: JSON-encoded description (HTML tags removed).
  - `{{ oct_price_microdata }}`: Product price (float).
  - `{{ oct_price_currency }}`: Currency code (e.g., 'UAH').
  - `{{ out_of_stock }}`: Boolean indicating if the product is out of stock.
- Example JSON-LD in your template:
  ```twig
  <script type="application/ld+json">
  {
      "@context": "https://schema.org",
      "@type": "Product",
      "name": {{ oct_micro_heading_title_json|raw }},
      "description": {{ oct_description_microdata_json|raw }},
      "offers": {
          "@type": "Offer",
          "price": {{ oct_price_microdata }},
          "priceCurrency": "{{ oct_price_currency }}",
          "availability": "{{ out_of_stock ? 'https://schema.org/OutOfStock' : 'https://schema.org/InStock' }}"
      }
  }
  </script>
  ```

### 4. Backup Recommendation
- Before making changes or testing, back up your site’s files (via FileZilla) and database (via phpMyAdmin).
- Test custom templates on a staging site to avoid disrupting your live store.

## How the Module Works
- **Template Selection**:
  - Retrieves the product’s categories using `$this->model_catalog_product->getCategories($product_id)`.
  - Checks if any category ID matches the `$custom_templates` array.
  - Sets the `$template` variable to the corresponding template path or defaults to `product/product`.
- **JSON-LD Data**:
  - Extracts the product name and description from `$product_info`.
  - Cleans the description by replacing `<br>` and `<br />` with spaces using `preg_replace`.
  - JSON-encodes the name and description with `JSON_UNESCAPED_UNICODE | JSON_UNESCAPED_SLASHES` for proper UTF-8 and URL handling.
  - Determines the price (special or regular) and casts it to a float to remove trailing zeros.
  - Retrieves the currency from the session, defaulting to 'UAH'.
  - Sets the out-of-stock status based on product quantity.
- **Output**:
  - Replaces the default template rendering line (`$this->response->setOutput($this->load->view('product/product', $data))`) with the dynamic `$template` variable.

## Technical Details
- **Version**: 1.5
- **Compatibility**: ocStore 3.0.3.7, OpenCart 3.x (test on other versions).
- **PHP**: 7.3 or higher.
- **OCMOD**: Modifies `catalog/controller/product/product.php` using two operations:
  1. Adds logic before the output line to set the template and prepare JSON-LD data.
  2. Replaces the default template path with the dynamic `$template`.
- **Security**: Uses standard OpenCart session and model methods, with no additional security concerns.
- **Encoding**: Supports UTF-8 for multilingual stores.
- **Dependencies**: Requires the `catalog/model/catalog/product.php` model to retrieve categories and the existence of custom template files.

## Limitations
- Custom templates must be created manually and placed in the theme’s template directory.
- Only supports categories defined in the `$custom_templates` array (e.g., category ID 468 for `product_generator`).
- Does not handle custom modules or non-standard product data fields.
- JSON-LD output requires proper integration in the Twig template to be effective.
- No automatic fallback for missing templates (ensure they exist).

## Code Structure
### OCMOD XML: `custom_category_template_jsonld_price.ocmod.xml`
- **File Modified**: `catalog/controller/product/product.php`
- **Operations**:
  1. **Before Output**:
     - Adds logic to check product categories and assign a custom template.
     - Prepares JSON-LD data (name, description, price, currency, stock status).
     - Example code added:
       ```php
       $template = 'product/product';
       if (isset($product_info)) {
           $categories = $this->model_catalog_product->getCategories($this->request->get['product_id']);
           $custom_templates = [
               468 => 'product/product_generator',
               // 455 => 'product/product_ebike',
               // 785 => 'product/product_escooter'
           ];
           if ($categories) {
               foreach ($categories as $category) {
                   if (isset($custom_templates[$category['category_id']])) {
                       $template = $custom_templates[$category['category_id']];
                       break;
                   }
               }
           }
           // JSON-LD fields
           $data['oct_micro_heading_title'] = $product_info['name'];
           $data['oct_description_microdata'] = html_entity_decode($product_info['description'], ENT_QUOTES, 'UTF-8');
           $clean_description = preg_replace('#<br\s*/?>#i', ' ', $data['oct_description_microdata']);
           $data['oct_micro_heading_title_json'] = json_encode($data['oct_micro_heading_title'], JSON_UNESCAPED_UNICODE | JSON_UNESCAPED_SLASHES);
           $data['oct_description_microdata_json'] = json_encode(strip_tags($clean_description), JSON_UNESCAPED_UNICODE | JSON_UNESCAPED_SLASHES);
           $data['text_buy_description'] = sprintf(
               $this->language->get('text_buy_description'),
               $product_info['name'],
               $product_info['name']
           );
           $price = $product_info['special'] ?: $product_info['price'];
           $data['oct_price_microdata'] = (float) $price;
           $data['oct_price_currency'] = $this->session->data['currency'] ?? 'UAH';
           $data['out_of_stock'] = ($product_info['quantity'] <= 0);
       }
       ```
  2. **Replace Output**:
     - Replaces `$this->response->setOutput($this->load->view('product/product', $data))` with:
       ```php
       $this->response->setOutput($this->load->view($template, $data));
       ```
     - Uses the dynamic `$template` variable to load the appropriate template.

## Requirements
- ocStore/OpenCart 3.0.3.7 (or compatible OpenCart 3.x version).
- PHP 7.3 or higher.
- Custom template files in `catalog/view/theme/your_theme/template/product/`.
- OCMOD system enabled in the admin panel.

## Author
- webitproff — [GitHub](https://github.com/webitproff)
- Date: October 12, 2025
- Project: [oc-custom_category_template_jsonld_price](https://github.com/webitproff/oc-custom_category_template_jsonld_price)

## License
BSD License

## 🛟 Support and Contributions
- Create issues: [GitHub Issues](https://github.com/webitproff/oc-custom_category_template_jsonld_price/issues)
- Pull requests are welcome.

___

# Утилита кастомизации шаблонов категорий + JSON-LD + Цена для ocStore / OpenCart

## Модуль для кастомных шаблонов страниц товаров с JSON-LD микроразметкой и улучшениями цен

[![Лицензия](https://img.shields.io/badge/лицензия-BSD-blue.svg)](https://github.com/webitproff/oc-custom_category_template_jsonld_price/blob/main/LICENSE)
[![Версия](https://img.shields.io/badge/версия-1.5-green.svg)](https://github.com/webitproff/oc-custom_category_template_jsonld_price/releases)
[![Совместимость с ocStore](https://img.shields.io/badge/ocStore-3.0.3.7-orange.svg)](https://ocstore.com/)
[![PHP](https://img.shields.io/badge/PHP-7.3-blueviolet.svg)](https://www.php.net/releases/7_3_0.php)

## Общая информация
**Custom Category Template + JSON-LD + Price** — это бесплатный модуль на основе OCMOD для ocStore/OpenCart, который улучшает страницы товаров за счёт:
1. Назначения кастомных шаблонов для товаров в зависимости от их категории.
2. Добавления JSON-LD микроразметки для улучшения SEO.
3. Включения информации о цене и валюте для структурированных данных.
4. Отображения статуса отсутствия товара на складе.

Модуль модифицирует контроллер страницы товара (`catalog/controller/product/product.php`), чтобы динамически выбирать шаблоны для определённых категорий товаров и добавлять JSON-LD структурированные данные для поисковой оптимизации. Модуль протестирован с **ocStore 3.0.3.7 + PHP 7.3**, но может работать с другими версиями OpenCart 3.x (тестируйте на копии сайта).

### 👀 [Посмотреть в маркетплейсе](https://abuyfile.com/en/market/opencart/oc-mods/custom-product-page-templates-for-category-on-ocstore-opencart)

## Введение для новичков
Модуль **Custom Category Template + JSON-LD + Price** настраивает отображение страниц товаров в интернет-магазине на ocStore/OpenCart. Он позволяет использовать разные шаблоны для товаров в определённых категориях (например, уникальный шаблон для «Генераторов») и добавляет структурированные данные (JSON-LD) для улучшения восприятия страниц поисковыми системами, такими как Google. Также модуль включает информацию о цене и наличии товаров для улучшения SEO и пользовательского опыта.

**Зачем это нужно?**
- **Кастомные шаблоны**: Товары в разных категориях (например, генераторы, электровелосипеды или электросамокаты) могут требовать уникального дизайна или макета. Этот модуль позволяет назначить определённые шаблоны для товаров в зависимости от их категории.
- **Улучшение SEO**: JSON-LD микроразметка помогает поисковым системам отображать расширенные сниппеты (например, название товара, цена и наличие) в результатах поиска, повышая видимость.
- **Цена и наличие**: Добавляет цену (включая акционные цены) и статус наличия для отображения или использования в шаблонах.

**Важно для новичков**: **Всегда создавайте резервную копию сайта** (файлы и база данных) перед установкой модуля. Используйте FileZilla для файлов и phpMyAdmin для базы данных, чтобы можно было восстановить сайт в случае проблем.

### Почему это важно
- **Улучшенный пользовательский опыт**: Кастомные шаблоны позволяют адаптировать дизайн под разные типы товаров, улучшая взаимодействие клиентов с магазином.
- **Преимущества для SEO**: JSON-LD микроразметка может улучшить позиции в поисковой выдаче и повысить кликабельность за счёт структурированной информации о товарах.
- **Гибкость**: Модуль легко расширяем для дополнительных категорий или шаблонов без значительных изменений кода.

## Основные возможности
- Динамическое назначение кастомных шаблонов для товаров в зависимости от ID категории.
- Добавление JSON-LD микроразметки для названия товара, описания, цены и валюты.
- Обработка акционных цен (скидок) с возвратом к обычной цене, если акционная отсутствует.
- Индикация статуса отсутствия товара на складе (количество ≤ 0).
- Обработка описаний товаров: удаление HTML-тегов и замена `<br>` на пробелы для чистого вывода в JSON-LD.
- Использование OCMOD для бесшовной интеграции без переписывания основных файлов.
- Поддержка кодировки UTF-8 для многоязычных магазинов.
- Лёгкий и целенаправленный модуль, изменяющий только контроллер страницы товара.

## Структура файлов модуля
Модуль представляет собой OCMOD XML-файл, который изменяет файл `catalog/controller/product/product.php`. Дополнительных файлов модуль не включает, но он ссылается на кастомные шаблоны, которые должны существовать в директории `catalog/view/theme/your_theme/template/product/`.

```
catalog/
├── controller/
│   └── product/
│       └── product.php # Модифицируется OCMOD для добавления логики шаблонов и JSON-LD
├── view/
│   └── theme/
│       └── your_theme/
│           └── template/
│               └── product/
│                   ├── product.twig # Шаблон по умолчанию
│                   └── product_generator.twig # Пример кастомного шаблона для категории ID 468
```

## Требования
Убедитесь, что ваш магазин соответствует этим требованиям:
- **ocStore/OpenCart**: Версия 3.0.3.7 (другие версии OpenCart 3.x могут работать, но тестируйте на копии сайта).
- **PHP**: Версия 7.3. Проверьте в админ-панели: «Система» → «Информация о сервере» → найдите «PHP Version».
- **Доступ к файлам**: Требуется FTP (через FileZilla) или доступ через панель хостинга (cPanel, DirectAdmin и т.д.) для загрузки OCMOD-файла и кастомных шаблонов.
- **Кастомные шаблоны**: Файлы кастомных шаблонов (например, `product_generator.twig`) должны существовать в директории шаблонов вашей темы.
- **База данных**: MySQL или MariaDB, доступ через phpMyAdmin для резервного копирования.
- **Тема**: Магазин должен использовать тему, поддерживающую шаблоны Twig.

**Как узнать версию PHP?**
1. Войдите в админ-панель.
2. Перейдите в «Система» → «Информация о сервере».
3. Найдите строку «PHP Version». Если версия не 7.3, обратитесь к хостинг-провайдеру для обновления.

## Подробная инструкция по установке
Следуйте этим шагам, чтобы установить модуль. Инструкция подходит как для новичков, так и для опытных пользователей.

### 1. Скачивание модуля
- Перейдите на страницу проекта на GitHub: [https://github.com/webitproff/oc-custom_category_template_jsonld_price](https://github.com/webitproff/oc-custom_category_template_jsonld_price).
- Нажмите «Code» → «Download ZIP» и распакуйте архив или скачайте OCMOD XML-файл напрямую.
- Для продвинутых пользователей: клонируйте репозиторий: `git clone https://github.com/webitproff/oc-custom_category_template_jsonld_price.git`.

### 2. Подготовка кастомных шаблонов
- Убедитесь, что кастомные шаблоны (например, `product_generator.twig`) существуют в директории вашей темы: `catalog/view/theme/your_theme/template/product/`.
- Пример: Для категории ID 468 создайте `product_generator.twig`, основанный на стандартном шаблоне `product.twig`, и настройте его по вашим требованиям.
- Если кастомные шаблоны отсутствуют, модуль вернётся к стандартному шаблону `product/product.twig` или выдаст ошибку. Поэтому следует сразу клонировать ваш шублон страницы карточки товара `product.twig` и переименовать его по примеру `product_cat_name.twig`, затем устанавливаем модуль

### 3. Загрузка OCMOD-файла
- Войдите в админ-панель ocStore/OpenCart.
- Перейдите в **Расширения → Установщик расширений**.
- Нажмите **Загрузить** и выберите OCMOD XML-файл (например, `custom_category_template_jsonld_price.ocmod.xml`).
- Дождитесь успешного завершения загрузки.

### 4. Установка модуля
- Перейдите в **Расширения → Модификаторы**.
- Найдите в списке «Custom Category Template + JSON-LD + Price».
- Нажмите кнопку **Обновить** (иконка с круговыми стрелками), чтобы применить изменения OCMOD.
- Убедитесь, что модификатор включен (зелёная галочка).

### 5. Очистка кэша
- Перейдите в **Система → Инструменты → Менеджер кэша** (или аналогичный раздел в вашей админ-панели).
- Очистите кэш системы и кэш шаблонов, чтобы изменения вступили в силу.

### 6. Проверка установки
- Откройте страницу товара, принадлежащего категории с кастомным шаблоном (например, категория ID 468).
- Проверьте исходный код страницы (ПКМ → «Просмотреть код страницы»), чтобы найти JSON-LD микроразметку в теге `<script type="application/ld+json">`.
- Убедитесь, что загружается правильный шаблон (например, `product_generator.twig` для категории ID 468).

## Использование модуля
### 1. Назначение кастомных шаблонов
- Модуль получает категории товара с помощью `$this->model_catalog_product->getCategories($product_id)`.
- Использует предопределённый массив для сопоставления ID категорий с кастомными шаблонами:
  ```php
  $custom_templates = [
      468 => 'product/product_generator',
      // 455 => 'product/product_ebike',
      // 785 => 'product/product_escooter'
  ];
  ```
- Если товар принадлежит категории, указанной в `$custom_templates`, модуль использует соответствующий шаблон (например, `product/product_generator` для категории ID 468). В противном случае используется стандартный шаблон `product/product`.
- Чтобы добавить дополнительные шаблоны, отредактируйте массив `$custom_templates` в OCMOD XML-файле, раскомментировав или добавив новые записи для других ID категорий и их шаблонов.

### 2. JSON-LD микроразметка
- Модуль добавляет следующие данные на страницу товара для JSON-LD:
  - **Название товара**: `$data['oct_micro_heading_title']` и его JSON-кодированная версия `$data['oct_micro_heading_title_json']`.
  - **Описание**: `$data['oct_description_microdata']` (декодированное HTML) и `$data['oct_description_microdata_json']` (без HTML-тегов, с заменой `<br>` на пробелы).
  - **Цена**: `$data['oct_price_microdata']` (использует акционную цену, если она есть, иначе обычную, приведённую к типу float).
  - **Валюта**: `$data['oct_price_currency']` (по умолчанию 'UAH', если валюта не установлена в сессии).
  - **Статус наличия**: `$data['out_of_stock']` (true, если количество товара ≤ 0).
- Эти переменные доступны в вашем Twig-шаблоне для отображения JSON-LD структурированных данных.

### 3. Настройка шаблонов
- В кастомном шаблоне (например, `product_generator.twig`) вы можете использовать новые переменные:
  - `{{ oct_micro_heading_title }}`: Название товара.
  - `{{ oct_description_microdata }}`: Полное описание (с HTML).
  - `{{ oct_micro_heading_title_json }}`: JSON-кодированное название.
  - `{{ oct_description_microdata_json }}`: JSON-кодированное описание (без HTML-тегов).
  - `{{ oct_price_microdata }}`: Цена товара (float).
  - `{{ oct_price_currency }}`: Код валюты (например, 'UAH').
  - `{{ out_of_stock }}`: Булево значение, указывающее, отсутствует ли товар на складе.
- Пример JSON-LD в шаблоне:
  ```twig
  <script type="application/ld+json">
  {
      "@context": "https://schema.org",
      "@type": "Product",
      "name": {{ oct_micro_heading_title_json|raw }},
      "description": {{ oct_description_microdata_json|raw }},
      "offers": {
          "@type": "Offer",
          "price": {{ oct_price_microdata }},
          "priceCurrency": "{{ oct_price_currency }}",
          "availability": "{{ out_of_stock ? 'https://schema.org/OutOfStock' : 'https://schema.org/InStock' }}"
      }
  }
  </script>
  ```

### 4. Рекомендация по резервному копированию
- Перед внесением изменений или тестированием создайте резервную копию файлов сайта (через FileZilla) и базы данных (через phpMyAdmin).
- Тестируйте кастомные шаблоны на тестовом сайте, чтобы не нарушить работу основного магазина.

## Принцип работы модуля
- **Выбор шаблона**:
  - Получает категории товара с помощью `$this->model_catalog_product->getCategories($product_id)`.
  - Проверяет, соответствует ли ID категории массиву `$custom_templates`.
  - Устанавливает переменную `$template` с путём к соответствующему шаблону или использует по умолчанию `product/product`.
- **JSON-LD данные**:
  - Извлекает название и описание товара из `$product_info`.
  - Очищает описание, заменяя `<br>` и `<br />` на пробелы с помощью `preg_replace`.
  - Кодирует название и описание в JSON с использованием `JSON_UNESCAPED_UNICODE | JSON_UNESCAPED_SLASHES` для корректной обработки UTF-8 и URL.
  - Определяет цену (акционную или обычную) и приводит её к типу float для удаления лишних нулей.
  - Получает валюту из сессии, по умолчанию 'UAH'.
  - Устанавливает статус отсутствия на складе на основе количества товара.
- **Вывод**:
  - Заменяет строку рендеринга шаблона по умолчанию (`$this->response->setOutput($this->load->view('product/product', $data))`) на динамическую переменную `$template`.

## Технические детали
- **Версия**: 1.5
- **Совместимость**: ocStore 3.0.3.7, OpenCart 3.x (тестируйте на других версиях).
- **PHP**: 7.3 или выше.
- **OCMOD**: Модифицирует `catalog/controller/product/product.php` с помощью двух операций:
  1. Добавляет логику перед строкой вывода для установки шаблона и подготовки JSON-LD данных.
  2. Заменяет путь к шаблону по умолчанию на динамическую переменную `$template`.
- **Безопасность**: Использует стандартные методы сессий и моделей OpenCart, без дополнительных уязвимостей.
- **Кодировка**: Поддерживает UTF-8 для многоязычных магазинов.
- **Зависимости**: Требуется модель `catalog/model/catalog/product.php` для получения категорий и наличие кастомных шаблонов.

## Ограничения
- Кастомные шаблоны должны создаваться вручную и размещаться в директории шаблонов темы.
- Поддерживает только категории, указанные в массиве `$custom_templates` (например, ID 468 для `product_generator`).
- Не учитывает кастомные модули или нестандартные поля данных товаров.
- Для эффективного использования JSON-LD требуется правильная интеграция в Twig-шаблон.
- Нет автоматического возврата к запасному шаблону, если кастомный шаблон отсутствует (убедитесь, что он существует).

## Структура кода
### OCMOD XML: `custom_category_template_jsonld_price.ocmod.xml`
- **Изменяемый файл**: `catalog/controller/product/product.php`
- **Операции**:
  1. **Перед выводом**:
     - Добавляет логику для проверки категорий товара и назначения кастомного шаблона.
     - Подготавливает JSON-LD данные (название, описание, цена, валюта, статус наличия).
     - Пример добавленного кода:
       ```php
       $template = 'product/product';
       if (isset($product_info)) {
           $categories = $this->model_catalog_product->getCategories($this->request->get['product_id']);
           $custom_templates = [
               468 => 'product/product_generator',
               // 455 => 'product/product_ebike',
               // 785 => 'product/product_escooter'
           ];
           if ($categories) {
               foreach ($categories as $category) {
                   if (isset($custom_templates[$category['category_id']])) {
                       $template = $custom_templates[$category['category_id']];
                       break;
                   }
               }
           }
           // JSON-LD поля
           $data['oct_micro_heading_title'] = $product_info['name'];
           $data['oct_description_microdata'] = html_entity_decode($product_info['description'], ENT_QUOTES, 'UTF-8');
           $clean_description = preg_replace('#<br\s*/?>#i', ' ', $data['oct_description_microdata']);
           $data['oct_micro_heading_title_json'] = json_encode($data['oct_micro_heading_title'], JSON_UNESCAPED_UNICODE | JSON_UNESCAPED_SLASHES);
           $data['oct_description_microdata_json'] = json_encode(strip_tags($clean_description), JSON_UNESCAPED_UNICODE | JSON_UNESCAPED_SLASHES);
           $data['text_buy_description'] = sprintf(
               $this->language->get('text_buy_description'),
               $product_info['name'],
               $product_info['name']
           );
           $price = $product_info['special'] ?: $product_info['price'];
           $data['oct_price_microdata'] = (float) $price;
           $data['oct_price_currency'] = $this->session->data['currency'] ?? 'UAH';
           $data['out_of_stock'] = ($product_info['quantity'] <= 0);
       }
       ```
  2. **Замена вывода**:
     - Заменяет `$this->response->setOutput($this->load->view('product/product', $data))` на:
       ```php
       $this->response->setOutput($this->load->view($template, $data));
       ```
     - Использует динамическую переменную `$template` для загрузки нужного шаблона.

## Требования
- ocStore/OpenCart 3.0.3.7 (или совместимая версия OpenCart 3.x).
- PHP 7.3 или выше.
- Кастомные шаблоны в директории `catalog/view/theme/your_theme/template/product/`.
- Включённая система OCMOD в админ-панели.

## Автор
- webitproff — [GitHub](https://github.com/webitproff)
- Дата: 12 октября 2025
- Проект: [oc-custom_category_template_jsonld_price](https://github.com/webitproff/oc-custom_category_template_jsonld_price)

## Лицензия
BSD License

## 🛟 Поддержка и вклад
- Создавайте issue: [GitHub Issues](https://github.com/webitproff/oc-custom_category_template_jsonld_price/issues)
- Pull request приветствуются.
