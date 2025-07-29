# Angular Nx Module Federation Workspace

This guide walks you through setting up a workspace using [Nx](https://nx.dev) with Angular and Module Federation, including a **host app** and two **remote apps** (`nav` and `details`).

---

## 📦 Create Nx Workspace

```bash
mkdir angular-nx-mf
cd angular-nx-mf
npx create-nx-workspace@latest module-fed --preset=apps
```

**Prompt answers:**

- `Which CI provider would you like to use?` → `skip`
- `Would you like remote caching to make your build faster?` → `skip`

---

## ▶️ Set Up Angular

Navigate into your new workspace:

```bash
cd module-fed
```

Add Angular support:

```bash
npx nx add @nx/angular
```

> **Prompt:** `Install Nx Console?` → `false`

---

## 🏗️ Generate Host and Remote Apps

Use the Nx Angular host generator to create a **shell** app and link two remote apps: `nav` and `details`.

```bash
npx nx g @nx/angular:host apps/shell --remotes="nav,details"
```

**Prompt answers:**

- `Which stylesheet format would you like to use?` → `scss`
- `Which unit test runner would you like to use?` → `none`
- `Which E2E test runner would you like to use?` → `none`

---

## 🚀 Serve the Host with Remotes

To run the host (`shell`) with the remote apps (`nav`, `details`):

```bash
npx nx serve shell -o --devRemotes="nav,details"
```

This will open the `shell` app in the browser with Module Federation configured and working.

---

## 📁 Project Structure

```
module-fed/
├── apps/
│   ├── shell/     # Host application
│   ├── nav/       # Remote application 1
│   └── details/   # Remote application 2
├── libs/          # Shared libraries (optional)
└── ...
```

---

## ✅ Next Steps

- Implement lazy-loaded routes between host and remotes
- Share common libraries using `@nx/angular:module-federation`
- Add state management, services, or UI libraries
- Set up CI/CD, linting, testing as needed

---

## 🔗 Resources

- [Nx Documentation](https://nx.dev/angular)
- [Module Federation Guide](https://nx.dev/recipes/module-federation)
- [Angular CLI](https://angular.io/cli)

---

Happy coding! 🎉
