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
