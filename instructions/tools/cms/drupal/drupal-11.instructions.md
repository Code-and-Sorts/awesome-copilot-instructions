# GitHub Copilot Instructions

These instructions define how GitHub Copilot should assist with this Drupal project. The goal is to ensure consistent, high-quality code generation aligned with Drupal conventions, security best practices, and our development standards.

## 🧠 Context

- **Project Type**: Content Management System / Website / Web Application
- **Platform**: Drupal 11
- **Framework / Libraries**: Symfony Components / Drupal Core APIs
- **Database**: MySQL / MariaDB
- **Backend**: PHP
- **Frontend**: Twig / HTML / CSS / JavaScript
- **Development Environment**: DDEV
- **Command runner**: just
- **Architecture**: Modular / Hook-based / Entity-driven / Service-oriented

## 🔧 General Guidelines

- Follow Drupal coding standards and best practices (PSR-2, Drupal's PHP standards).
- Use Drupal's APIs instead of direct database queries or PHP built-ins when possible.
- Implement proper access control and security measures for all functionality.
- Use dependency injection and services for reusable business logic.
- Follow the "Drupal way" - leverage existing systems rather than reinventing.
- Use `drupal/coder` for code formatting and standards compliance.
- Document all public functions with proper PHPDoc comments.
- Prefer vanilla JavaScript over jQuery - use modern ES6+ features and native DOM APIs.
- Use Drupal's JavaScript API and behaviors (`Drupal.behaviors`) for frontend functionality.

## 📁 File Structure

Use this structure as a guide when creating or updating files:

```text
web/
  modules/
    custom/
      my_module/
        src/
          Controller/
          Entity/
          Form/
          Plugin/
          Service/
        templates/
        js/
        config/
          install/
          schema/
        my_module.info.yml
        my_module.module
        my_module.routing.yml
        my_module.services.yml
        my_module.libraries.yml
  themes/
    custom/
      my_theme/
        src/
        templates/
        css/
        js/
        images/
        my_theme.info.yml
        my_theme.theme
        my_theme.libraries.yml
config/
  sync/
    core.entity_form_display.*
    core.entity_view_display.*
    views.view.*
```

## 🧶 Patterns

### ✅ Patterns to Follow

- Use Drupal's Entity API for data modeling and storage.
- Implement hook functions following naming conventions (`hook_form_alter`, `hook_theme`, etc.).
- Use Services and Dependency Injection for business logic.
- Create Configuration entities for admin-configurable functionality.
- Use Form API for all user input forms with proper validation and security.
- Implement proper caching using Cache API (`#cache` render arrays, cache tags).
- Use Translation API (`t()`, `\Drupal::translation()`) for all user-facing strings.
- Follow security best practices - sanitize output, validate input, check permissions.
- Use Render API for all HTML output (`#type`, `#theme`, render arrays).
- Create Plugin systems for extensible functionality.
- Implement JavaScript using `Drupal.behaviors` for proper initialization and AJAX compatibility.

### 🚫 Patterns to Avoid

- Don't use direct database queries - use Entity API or Database API.
- Avoid hardcoded strings - use configuration or translation functions.
- Don't output raw HTML - use render arrays and proper theming.
- Avoid bypassing Drupal's security layer or permission system.
- Don't use global variables - use dependency injection or services.
- Avoid writing to files outside of designated directories.
- Don't ignore caching - implement proper cache invalidation.
- Avoid mixing business logic with presentation layer.
- Don't use jQuery unless absolutely necessary - prefer vanilla JavaScript and modern DOM APIs.

## 🧪 Testing Guidelines

- Use PHPUnit for unit testing custom functionality.
- Write Kernel tests for testing Drupal-integrated functionality.
- Use Functional tests (BrowserTestBase) for full page testing.
- Test with SimpleTest or Drupal Test Traits for legacy compatibility.
- Mock external services and dependencies in unit tests.
- Test access control and permissions thoroughly.
- Include tests for form validation and submission.

## 🧩 Example Prompts

- `Copilot, create a custom Drupal module that adds a content type for events with date fields and location.`
- `Copilot, implement a Drupal form that collects user feedback and saves it as a custom entity.`
- `Copilot, write a Drupal hook_form_alter to add custom validation to the user registration form.`
- `Copilot, create a Drupal service that integrates with an external API and caches the results.`
- `Copilot, generate a Drupal theme template that displays a custom content type with proper field rendering.`
- `Copilot, write a Drupal configuration entity for storing API settings with a settings form.`
- `Copilot, implement a custom Drupal field type for storing and displaying social media links.`
- `Copilot, create a Drupal behavior using vanilla JavaScript to add interactive functionality to a form.`
- `Copilot, implement a JavaScript function using fetch() API to make AJAX calls to a Drupal REST endpoint.`

## 🔁 Iteration & Review

- Always validate Copilot output against Drupal coding standards using `drupal/coder`.
- Test all functionality in a local Drupal environment before committing.
- Review security implications of any custom code, especially user input handling.
- Use `drush` commands to clear caches and test configuration changes.
- Ensure all custom code follows Drupal's API patterns and conventions.
- Verify proper access control and permission checks are in place.

## 📚 References

- [Drupal API Documentation](https://api.drupal.org/)
- [Drupal Coding Standards](https://www.drupal.org/docs/develop/standards/coding-standards)
- [Drupal JavaScript Coding Standards](https://www.drupal.org/docs/develop/standards/javascript)
- [Drupal JavaScript API and Behaviors](https://www.drupal.org/docs/drupal-apis/javascript-api)
- [Managing JavaScript in Drupal](https://www.drupal.org/docs/theming-drupal/adding-stylesheets-css-and-javascript-js-to-a-drupal-theme)
- [Drupal Security Best Practices](https://www.drupal.org/docs/security-in-drupal)
- [Form API Reference](https://api.drupal.org/api/drupal/core%21core.api.php/group/form_api)
- [Entity API Documentation](https://www.drupal.org/docs/drupal-apis/entity-api)
- [Render API Documentation](https://api.drupal.org/api/drupal/core%21core.api.php/group/render)
- [Hook System Documentation](https://api.drupal.org/api/drupal/core%21core.api.php/group/hooks)
- [Services and Dependency Injection](https://www.drupal.org/docs/drupal-apis/services-and-dependency-injection)
- [Configuration API](https://www.drupal.org/docs/drupal-apis/configuration-api)
- [Testing in Drupal](https://www.drupal.org/docs/testing)
- [Drupal Console](https://drupalconsole.com/)
- [Drush Documentation](https://www.drush.org/)
- [DDEV Documentation](https://ddev.readthedocs.io/en/stable/)
- [Just a command runner](https://github.com/casey/just)
