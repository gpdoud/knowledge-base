# Angular

There are two production versions of Angular: AngularJs and Angular.

AngularJs is the v1 release. It is a Javascript-based product and was very good at creating single applications. But did not allow sharing code with other applications.

Angular is the v2 and all later releases. It was rearchitected to be component-based making it more reusable across projects and was written with and uses Typescript rather than Javascript.

The two versions are functionally similar but syntactically different.

## Installation

Angular is installed using the Node Package Manager (npm) which is included with NodeJs.org.

Install the LTS version of `NodeJs.org`. (you many have to restart your machine)

Install the Angular CLI. This is used to create projects, build projects, create production applications,  and generate all the object used by Angular applications.

    npm i -g @angular/cli

## Upgrading an existing project

Upgrading an Angular project is usually easy but usually must be done by a single version upgrade at a time. Meaning, for a v10 project to be upgraded to v15, it must first be upgraded to v11, then v12, then v13, then v14, and finally v15.

    ng upgrade @angular/core@XX @angular/cli@XX

Where XX is the version up upgrade to.

## Standalone Components (requires v15)

Standalone components execute without any NgModule.

1. Create a project as usual

    ng new <my-app>

2. Generate a standalone component

    ng g c my-page --standalone --flat --inline-style --inline-template

3. Delete the following files:
    
    app.module.ts
    app.component.ts,html,css

4. Update the `main.ts`

    import {bootstrapApplication} from '@angular/platform-browser';
    import {MyPageComponent} from './app/my-page.component';

    bootstrapApplication(MyPageComponent);
 
5. Update the `index.html`

    <app-my-page></app-my-page>

6. Standalone Component Code

```ng
@Component({
    standalone: true,
    selector: "app-my-page",
    template: `
        <h1>{{ title }}</h1>
    `,
    styles: [
        "h1 { color: blue; }"
    ]
})
export class AppMyPageComponent {
    title = "My Standalone Component";
}
```