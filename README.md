# PostCSS-Tailwind

## Basic PostCSS + Tailwind configuration

To use PostCSS from your command-line interface or with npm scripts there is postcss-cli.

```
npm i -D postcss postcss-cli autoprefixer tailwindcss
```

Create your tailwind.config.js

```
npx tailwindcss init
```

Add Tailwind and autoprefixer to your PostCSS configuration postcss.config.js file.

```
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  }
}
```

Add the paths to all of your template files in your tailwind.config.js file.

```
module.exports = {
  content: ["./src/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

Add the Tailwind directives to your CSS

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

To run multiple npm-scripts in parallel I like npm-run-all.

```
npm i -D npm-run-all
```

Having the page reload automatically after changes to files can accelerate development so lets add live-server into the project.
If you are a Linux user you must use a admin user as root or have permission to use 'sudo'

```
npm install -g live-server
```

Now lets configure npm script

```
"scripts": {
    "build:css": "postcss src/main.css -o public/style.css",
    "watch": "postcss src/main.css -o public/style.css -w",
    "live-server": "live-server",
    "dev": "npm-run-all --parallel watch live-server"
  },
```

For development we run.

```
npm run dev
```

For production we run.

```
npm run build:css
```
