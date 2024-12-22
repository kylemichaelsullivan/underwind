=== Underwind ===

Contributors: automattic
Tags: custom-background, custom-logo, custom-menu, featured-images, threaded-comments, translation-ready

Requires at least: 4.5
Tested up to: 5.4
Requires PHP: 5.6
Stable tag: 1.0.0
License: GNU General Public License v2 or later
License URI: LICENSE

A starter theme called Underwind.

== Description ==

Description

== Installation ==

1. In your admin panel, go to Appearance > Themes and click the Add New button.
2. Click Upload Theme and Choose File, then select the theme's .zip file. Click Install Now.
3. Click Activate to use your new theme right away.

== Frequently Asked Questions ==

= Does this theme support any plugins? =

Underwind includes support for WooCommerce and for Infinite Scroll in Jetpack.

= I saw this error in my console! What should I do?
cdn.tailwindcss.com should not be used in production. To use Tailwind CSS in production, install it as a PostCSS plugin or use the Tailwind CLI: https://tailwindcss.com/docs/installation

Tailwind was initialized on this theme via the Tailwind CDN in header.php. Read the next answer.

= I saw `keyWord` in header.php, and I want to install Tailwind properly.

1. Open your terminal and navigate to your theme directory:
   $ cd wp-content/themes/underwind

2. If you haven't already, initialize npm:
   $ npm init -y

3. Install Tailwind CSS, PostCSS CLI, and cssnano:
   $ npm install -D tailwindcss postcss-cli cssnano autoprefixer

4. Generate the Tailwind CSS configuration file:
   $ npx tailwindcss init

5. Edit `tailwind.config.js` to include the paths to your theme files that will contain Tailwind classes:
   export default {
     content: [
       "./header.php",
       "./footer.php",
       "./index.php",
       "./template-parts/**/*.php"
     ],
     theme: {
       extend: {},
     },
     plugins: [],
   };

6. Add the Tailwind directives to the top of style.css (after WP boilerplate comment):
   @tailwind base;
   @tailwind components;
   @tailwind utilities;

7. Create `postcss.config.js` file in your theme directory and add the following:
   export default {
     plugins: {
       tailwindcss: {},
       autoprefixer: {},
       cssnano: {}
     }
   };

8. Modify `package.json` to include a script for building minified CSS to `tailwind.min.css`:
   {
     "name": "underwind",
     "version": "1.0.0",
     "type": "module",
     "scripts": {
       "build:css": "tailwindcss build tailwind.css -o tailwind.css && postcss tailwind.css -o tailwind.min.css"
     },
     "devDependencies": {
       "tailwindcss": "^3.0.0",
       "autoprefixer": "^10.0.0",
       "cssnano": "^5.0.0",
       "postcss": "^8.0.0",
       "postcss-cli": "^8.0.0"
     }
   }

9. Run the build script:
   $ npm run build:css

10. Add the following to `functions.php` to enqueue the minified CSS file:
    add_action('wp_enqueue_scripts', function () {
      wp_enqueue_style('tailwind-css', get_template_directory_uri() . '/tailwind.min.css');
    });

== Changelog ==

= 1.0 - May 12 2015 =
* Initial release

== Credits ==

* Based on Underscores https://underscores.me/, (C) 2012-2020 Automattic, Inc., [GPLv2 or later](https://www.gnu.org/licenses/gpl-2.0.html)
* normalize.css https://necolas.github.io/normalize.css/, (C) 2012-2018 Nicolas Gallagher and Jonathan Neal, [MIT](https://opensource.org/licenses/MIT)
