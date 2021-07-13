# Neo observable input

Ergonomic, robust RxJS Observable inputs for Angular

## Background

See https://github.com/angular/angular/issues/5689

Similar to https://github.com/Futhark/ngx-observable-input and https://github.com/insidewhy/observable-input and https://github.com/insidewhy/observable-input, but works with type checking Angular inputs, and avoids the tree-shaking problems of decorators.

## Install

```
npm i neo-observable-input
```

## Usage

```ts
import { Component } from "@angular/core";
import { ObservableInputs } from "neo-observable-input";

@Component({ template: "" })
export class ExampleComponent {
  private readonly inputs = new ObservableInputs();

  @Input()
  color: string;
  color$ = this.inputs.observe(() => this.color);

  @Input()
  count: number;
  count$ = this.inputs.observe(() => this.count);

  ngOnChanges() {
    this.inputs.onChanges();
  }
}
```
