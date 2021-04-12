# code
codigos Javascript y Typescript

# Recorrer un objeto [Object]

      const lunch = this.formu.value;
      Object.keys(lunch).forEach(function (item) {
        console.log(item); // key
        console.log(lunch[item]); // value
      });
      

# Clonado array unidimensional
    // this.listaTemporal = this.lista; // Esto es paso por referencia y no es lo que queremos
    this.listaTemporal = [...this.lista]; // Clonado para arrays
    
# Clonado profundo array bidimensionales
    this.listaTemporal = JSON.parse(JSON.stringify(this.lista)); // Clonado profundo para matrices bidimensionales
    
https://www.freecodecamp.org/news/how-to-clone-an-array-in-javascript-1d3183468f6a/
    
# Mostrar un json usando *ngFor

      @Pipe({name: 'keys'})
      export class KeysPipe implements PipeTransform {
        transform(value, args:string[]) : any {
          let keys = [];
          for (let key in value) {
            keys.push({key: key, value: value[key]});
          }
          return keys;
        }
      }

      <span *ngFor="#entry of content | keys">           
        Key: {{entry.key}}, value: {{entry.value}}
      </span>

https://stackoverflow.com/questions/35647365/how-to-display-json-object-using-ngfor

# Asignar valores a campos no databinding
Por ejemplo:

    <div class="dropdown-menu">
        <button class="btn btn-link dropdown-item" [attr.data-column]="i" (click)="mostrar()"
            *ngFor="let col of cols; let i=index">{{col}}</button>
        <button class="btn btn-link dropdown-item">Columna2</button>
    </div>

      <div class="dropdown-menu">
          <button class="btn btn-link dropdown-item" data-column="0">Name</button>
          <button class="btn btn-link dropdown-item" data-column="1">Position</button>
          <button class="btn btn-link dropdown-item" data-column="2">Office</button>
          <button class="btn btn-link dropdown-item" data-column="3">Age</button>
          <button class="btn btn-link dropdown-item" data-column="4">Start date</button>
          <button class="btn btn-link dropdown-item" data-column="5">Salary</button>
          <button class="btn btn-link dropdown-item">Columna2</button>
      </div>

# Solucion compatibilidad Angular 7 vs @ng-select

Version 2.9.1 es compatible con Angular 7
Solución: npm i @ng-select/ng-select@2.9.1

https://www.npmjs.com/package/@ng-select/ng-select?activeTab=versions


# CLI Angular

*ng g m features*    

      /features
      CREATE src/app/features/features.module.ts (191 bytes)

*ng g m features/alerts --routing*

      CREATE src/app/features/alerts/alerts-routing.module.ts (249 bytes)
      CREATE src/app/features/alerts/alerts.module.ts (280 bytes)
      
*ng g c features/alerts/pages/alarm* 

      CREATE src/app/features/alerts/pages/alarm/alarm.component.html (20 bytes)
      CREATE src/app/features/alerts/pages/alarm/alarm.component.spec.ts (621 bytes)
      CREATE src/app/features/alerts/pages/alarm/alarm.component.ts (272 bytes)     
      CREATE src/app/features/alerts/pages/alarm/alarm.component.scss (0 bytes)     
      UPDATE src/app/features/alerts/alerts.module.ts (358 bytes)      
      
**ng g m features/alerts/pages/analysis -m=app --route analysis**

      CREATE src/app/features/alerts/pages/analysis/analysis-routing.module.ts (352 bytes)
      CREATE src/app/features/alerts/pages/analysis/analysis.module.ts (363 bytes)
      CREATE src/app/features/alerts/pages/analysis/analysis.component.html (23 bytes)
      CREATE src/app/features/alerts/pages/analysis/analysis.component.spec.ts (642 bytes)
      CREATE src/app/features/alerts/pages/analysis/analysis.component.ts (284 bytes)
      CREATE src/app/features/alerts/pages/analysis/analysis.component.scss (0 bytes)
      UPDATE src/app/app-routing.module.ts (374 bytes)
      
*ng g m products/product — flat -m app.module*

      — flat: NO nos cree otra carpeta products (ya tenemos una en el proyecto)
      
      -m app.module: expresa que queremos vincular el módulo recién creado con AppModule
      
*ng g m shared/shared — flat -m products/product.module*

      -m app.module expresa que queremos vincular el módulo recién creado con product/product.module

**ng g c modules/assets-management/views/installation-management -m modules/assets-management/assets-management.module**

      CREATE src/app/modules/assets-management/views/installation-management/installation-management.component.html (38 bytes)
      CREATE src/app/modules/assets-management/views/installation-management/installation-management.component.spec.ts (741 bytes)
      CREATE src/app/modules/assets-management/views/installation-management/installation-management.component.ts (337 bytes)
      CREATE src/app/modules/assets-management/views/installation-management/installation-management.component.scss (0 bytes)
      UPDATE src/app/modules/assets-management/assets-management.module.ts (2220 bytes)
