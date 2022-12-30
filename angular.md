# Angular

There are two production versions of Angular: `AngularJs` and `Angular`.

AngularJs is the v1 release. It is a Javascript-based product and was very good at creating single applications. But did not allow sharing code with other applications.

Angular is the v2 and all later releases. It was rearchitected to be component-based making it more reusable across projects and was written with and uses Typescript rather than Javascript.

The two versions are functionally similar but syntactically different.

## Installation

Angular is installed using the Node Package Manager (npm) which is included with NodeJs.org.

Install the LTS version of `NodeJs.org`. (you many have to restart your machine)

Install the Angular CLI. This is used to create projects, build projects, create production applications,  and generate all the object used by Angular applications.

```
npm i -g @angular/cli
```

## Upgrading an existing project

Upgrading an Angular project is usually easy but usually must be done by a single version upgrade at a time. Meaning, for a v10 project to be upgraded to v15, it must first be upgraded to v11, then v12, then v13, then v14, and finally v15.

```
ng upgrade @angular/core@XX @angular/cli@XX
```

Where XX is the version up upgrade to.

## Binding

One of the most productive features of Angular and all Javascript frameworks is _data binding_. It binds the data to the UI so the program does NOT have to copy the data to and from the UI.

Angular provides both one-way and two-way binding. One-way binding updates the UI whenever the data is changed but does not change the data when the UI is changed. This is used mostly when the UI using non-form controls to display the data. An example of this is displaying the data in a `<table>` which does not allow the user to change the data on the UI. Two-way binding allows the data to be changed either in the code or on the UI. If the data is changed in the code, the UI is updated. In addition, if the UI is updated, the data in the code is changed. Two-way binding is used when the data in the UI is using form controls like `<input>` or `<select>` tags. 

> Note: To use two-way binding, the project must import the `FormsModule` in the `app.module.ts` file and add the classname to the `imports` collection.

Here is an example of both:

```ts
// one-way binding
hello = "Hello to you!";
<label>{{ hello }}</label>
```

In the one-way binding, the property `hello` is set to a string. The `<label></label>` tag will display the string. The user cannot change the text in the label.

```ts
// two-way binding
name = "";
<input [(ngModel)]="name">
<label>Hello to {{ name }}</label>
```

In the two-way binding, the property `name` is set to an empty string then displayed in the `<input>` tag. The user can modify the text for the `name` and that will change the `name` property immediately. The `<label></label>` does one-way binding and will always display the current value of `name`.

## Modules

## Components

## Services

## Pipes

## Standalone Components (requires v15)

Standalone components execute without any NgModule.

1. Create a project as usual

```
ng new [my-app]
```

2. Generate a standalone component

```
ng g c my-page --standalone --flat --inline-style --inline-template
```

3. Delete the following files:

```ng    
app.module.ts
app.component.ts,html,css
```

4. Update the `main.ts`

```ts
import {bootstrapApplication} from '@angular/platform-browser';
import {MyPageComponent} from './app/my-page.component';

bootstrapApplication(MyPageComponent);
```

5. Update the `index.html`

```ts
<app-my-page></app-my-page>
```

6. Standalone Component Code

```ts
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