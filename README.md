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
    
    Otro ejemplo
    ------------
      let obj = { a: 1, b: 2, c: 3 };

      let objCopy = { ...obj }; // separa el objeto en una lista de parámetros
                                // luego devuelve el resultado en un nuevo objeto

      // ¿tienen los objetos el mismo contenido?
      alert(JSON.stringify(obj) === JSON.stringify(objCopy)); // true

      // ¿son iguales los objetos?
      alert(obj === objCopy); // false (no es la misma referencia)

      // modificando el objeto inicial no modifica la copia:
      obj.d = 4;
      alert(JSON.stringify(obj)); // {"a":1,"b":2,"c":3,"d":4}
      alert(JSON.stringify(objCopy)); // {"a":1,"b":2,"c":3}
      
      Esta manera de copiar un objeto es mucho más corta que let objCopy = Object.assign({}, obj); 
      o para un array let arrCopy = Object.assign([], arr); por lo que preferimos usarla siempre que podemos.
    
# Clonado profundo array bidimensionales
    this.listaTemporal = JSON.parse(JSON.stringify(this.lista)); // Clonado profundo para matrices bidimensionales (CON FECHAS NO FUNCIONA)
    this.tmpIntervals = _.cloneDeep(this.intervals) //Clonado profundo para arrays, objetos que contengan "FECHAS"
    
https://www.freecodecamp.org/news/how-to-clone-an-array-in-javascript-1d3183468f6a/    
    
# Operador Rest - Spread syntax (...)


      Cuando veamos "..." en el código, son los parámetros rest o el operador spread.
      Hay una manera fácil de distinguir entre ellos:

            Cuando ... se encuentra al final de los parámetros de una función, son los “parámetros rest” y recogen el resto de la lista de argumentos en un array.
            Cuando ... está en el llamado de una función o similar, se llama “operador spread” y expande un array en una lista.
            
      Patrones de uso:
      
            Los parámetros rest son usados para crear funciones que acepten cualquier número de argumentos.
            El operador spread es usado para pasar un array a funciones que normalmente requieren una lista de muchos argumentos.

                  function sum(x, y, z) {
                    return x + y + z;
                  }
                  const numbers = [2, 3, 4];
                  console.log(sum(1, ...numbers));
                  // Expected output: 6
                  console.log(sum.apply(null, numbers));
                  // Expected output: 9
    
    
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
      
**ng g c modules\widgets-home\components\widget-nodes -m modules\widgets-home\widgets-home.module.ts**

      CREATE src/app/modules/widgets-home/components/widget-nodes/widget-nodes.component.html (27 bytes)
      CREATE src/app/modules/widgets-home/components/widget-nodes/widget-nodes.component.spec.ts (664 bytes)     
      CREATE src/app/modules/widgets-home/components/widget-nodes/widget-nodes.component.ts (293 bytes)
      CREATE src/app/modules/widgets-home/components/widget-nodes/widget-nodes.component.scss (0 bytes)
      UPDATE src/app/modules/widgets-home/widgets-home.module.ts (2206 bytes)

# Descomposicion de un array en elementos 

      const data = { ...usuario };
      
# Cambiar a un brach anterior (sin afectar los cambios del brach actual)

      git reset --hard 78edd41fbe51c5b2a4e6016ebc10b68eb6824e53

# Linkar librerias a proyectos

      Desde la libreria
      cd dist/PROJECT_NAME
      npm link
      
      Desde el proyecto
      npm link LIBRARY_NAME
      
      Desde la libreria
      npm run buildlib --watch
      
      Fuente: https://dev.to/dontry/using-npm-link-in-angular9-11ie
      
# Fechas
*Hora actual en Israel "2023-04-12T20:37:02+03:00"*

      let dateTemp = moment().tz('Asia/Jerusalem').format();
      
*Hora actual de Israel en UTC "2023-04-12T17:37:02.000Z"*

      value = new Date(dateTemp).toISOString()
      
*Adaptar fecha de pantalla a timezone de destino antes de enviar a Back

      let dateMoment = moment().tz(timeZone);
      dateMoment.set({ year: date.getFullYear(), month: date.getMonth(), date: date.getDate(), hour: date.getHours(), minutes: date.getMinutes(), seconds: date.getSeconds(), milliseconds: date.getMilliseconds() });
      return dateMoment.toISOString();
      
*Otras funciones*

      let hora = moment(value).hour();
      let minute = moment(value).minute();
      value = moment(startDate).tz(this.jsonBuild.timeZone).set("hour", hora).set("minute", minute).set("second", 0).format();
      value = new Date(value).toLocaleString(this.jsonBuild.locale, {timeZone: this.jsonBuild.timeZone});
      value = new Date(value);
      
      let destinationFormat = moment(element.endDate).tz(this.jsonBuild.timeZone).set("hour", 23).set("minute", 59).set("second", 59).format();
      
      element.startDate = destinationFormat.substring(0, 11) + '00:00:00' + destinationFormat.substring(19, 26)
      element.endDate = this.moment(element.endDate).format().substring(0, 11) + '23:59:59' + destinationFormat.substring(19, 26)
      let hora = this.moment(element.startTime).hour();
      let minute = this.moment(element.startTime).minute();
      element.startTime = this.moment(element.startDate).tz(this.jsonBuild.timeZone).set("hour", hora).set("minute", minute).set("second", 0).format()
      
      <div>
        {{ loadInterval[info.mappingToDTO] ? (loadInterval[info.mappingToDTO] | date : info.format :
        loadInterval.id ? getOffset(info.mappingToDTO, loadInterval[info.mappingToDTO]) : null) : '-' }}
        <!-- {{ loadInterval[info.mappingToDTO] ? (loadInterval[info.mappingToDTO] | date : info.format : loadInterval.id ? '0120' : null) : '-' }}  -->
        <!-- {{ loadInterval[info.mappingToDTO] ? (loadInterval[info.mappingToDTO] | date : info.format) : '-' }}  -->
      </div>

# Test
      ng test --progress front_spa_fln
      ng test --progress @bomultimodal/modules-configuration
      ng test --progress @bomultimodal/modules-idi
      ng test --progress @crecbomh48/common-components
      
      Nota: front_spa_fln es el nombre que aparece en angular.json

      Para deshabilitar un test se pone una 'x' delante de it
      xit('should create', () => {
          expect(component).toBeTruthy();
      });

# SORT no ordena en Chrome
      // return obj.sort((a, b) => a[sortInformation.attribute] >= b[sortInformation.attribute]); //No funciona en Chrome
      // Solución
      return obj.sort(function (a, b) {
        if (a[sortInformation.attribute] > b[sortInformation.attribute]) {
          return 1;
        }
        if (a[sortInformation.attribute] < b[sortInformation.attribute]) {
          return -1;
        }
        // equals
        return 0;
      });

*Otra solucion*

      myArray.sort(function(a, b) {
        return a-b;
      });
      Note:not working when sort date in such a format "mm/dd/yyyy"

# Backticks
      const userInfo = `User info: ${name} ${surname} ${telephone}`;
      const userInfo = `User info: ${user.getName()} ${user.getEmail()}`;
      
# Regex
      "regex": {
            "hour": "/^([0-1]?[0-9]|2[0-3])$/",
            "minute": "/^([0-5]?[0-9])$/",
            "regexNumericField": "/^[0-9]+$/",
            "notOnlyWhiteSpace": "^(?!\\s*$).+"
          },
          defaultRegex = '^[0-9]+([.])?([0-9]+)?$'; //Numeros con decimales

          Desde JSON (validate mail)
          "pattern": "^(([^<>()\\[\\]\\.,;:\\s@]+(\\.[^<>()\\[\\]\\.,;:\\s@]+)*)|(.+))@((\\[[0-9]{1,3}\\.[0-9]{1,3}\\.[0-9]{1,3}\\.[0-9]{1,3}])|(([a-zA-Z\\-0-9]+\\.)+[a-zA-Z]{2,}))$"

# Snippets VSC
https://pablocianes.com/guardar-snippets-personalizados-en-visual-studio-code/
