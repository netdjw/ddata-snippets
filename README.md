# ddata-snippets

The ddata-snippets extension is for the `ddata-core`, `ddata-ui-input`, `ddata-ui-dialog` and `ddata-ui-common` npm packages.

This code snippets - as usual - made for speed up your work and help you keep the naming conventions.

## Keywords

### `!subscription`

The result:

```typescript
subscription: Subscription;
```

### `!loader:`

The result:

```typescript
loader: DataFactory = new DataFactory();
```

### `!loader.load`

The result:

```typescript
this.subscription = this.loader.load(
  [
    '',
  ],
  this,
  [this.helperService.getOne(this.model, this.isModal)]
).subscribe();
```

### `!init.data`

The result:

```typescript
data = !!data ? data : {};
```

### `!init.field`

The result:

```typescript
this.field = !!data.field ? data.field : '';
```

### `!init.array`

The result:

```typescript
// field
if (!!data.field && data.field instanceof Array) {
  data.field.forEach((element: any) => {
    this.field.push( new class().init(element) );
  });
}
```

### `!prepareToSave.field`

The result:

```typescript
field = !!this.field ? this.field : '',
```

### `!prepareToSave.array`

The result:

```typescript
// field
const field: any[] = [];
this.field.forEach((element: ClassNameInterface) => {
  field.push(element.prepareToSave());
});
```

### `!class`

The result:

```typescript
import { BaseModel, FieldContainerInterface, ID, ValidationRuleInterface } from 'ddata-core';
import { ClassNameInterface, ClassNameUIFieldsInterface } from './FileName.interface';

export class ClassName extends BaseModel implements ClassNameInterface {
  readonly api_endpoint = '/FileName';
  readonly model_name = 'ClassName';
  id: ID;

  validationRules: ValidationRuleInterface = {
  };

  fields: FieldContainerInterface<{ClassName}UIFieldsInterface>;

  init(data?: any): ClassNameInterface {
    data = !!data ? data : {};

    this.id = !!data.id ? data.id : 0;

    return this;
  }

  prepareToSave(): any {
    return {
      id: !!this.id ? this.id : 0,
    };
  }
}
```

### `!interface`

The result:

```typescript
import { BaseModelWithoutTypeDefinitionInterface, FieldsInterface, ID } from 'ddata-core';

export interface InterfaceNameUIFieldsInterface {
  name: string;
}

export interface InterfaceNameInterface extends
  InterfaceNameUIFieldsInterface,
  FieldsInterface<InterfaceNameUIFieldsInterface>,
  BaseModelWithoutTypeDefinitionInterface {

  id: ID;
}
```