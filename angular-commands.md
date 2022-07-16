# Angular CLI commands

- `ng (b)uild --prod { --baseHref="./" }` : Production build with optional base set to baseHref value (i.e. <base href="./">)

## Upgrading a version of Angular

- `ng upgrade @angular/cli@xx @angular/core@xx` : where xx is the major version number (i.e. 13 or 14)
- `npm update --legacy-peer-deps`

- May have to run `npm audit fix`