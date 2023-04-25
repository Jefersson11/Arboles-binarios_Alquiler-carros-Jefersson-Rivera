import java.util.Scanner;
public class Arbol_raiz_carros {
	

Nodo_vehiculos raiz;
private String color;
public Arbol_raiz_carros() {
this.raiz=null;
}public void Insertar(int _valor) {
Nodo_vehiculos nuevo = new Nodo_vehiculos(_valor);
if(raiz == null)
raiz = nuevo;
else {
Nodo_vehiculos padre=null;
Nodo_vehiculos actual = raiz;
while(actual !=null) {
padre=actual;
if(actual.valor > _valor) {
actual = actual.izq;
}else {
actual = actual.der;

}
}
if(padre.valor > _valor)
padre.izq = nuevo;
else
padre.der = nuevo;
}
}
public void Preorden(Nodo_vehiculos raiz2) {
if(raiz2 != null) {
System.out.print(raiz2.valor+"  ");
Preorden(raiz2.izq);
Preorden(raiz2.der);

}
}

public void Inorden(Nodo_vehiculos raiz2) {
if(raiz2 != null) {
Inorden(raiz2.izq);
System.out.print(raiz2.valor+ "  ");
Inorden(raiz2.der);

}
}

public void Posorden(Nodo_vehiculos raiz2) {
if(raiz2 !=null) {
Posorden(raiz2.izq);
   Posorden(raiz2.der);
System.out.print(raiz2.valor+ "  ");

}

}
public void Reemplazar (Nodo_vehiculos raiz2) {
Nodo_vehiculos p = raiz2;
Nodo_vehiculos a = raiz2.izq;
while(a.der  !=null) {
p = a;
a = a.der;
}
raiz2.valor = a.valor;
System.out.println(a.valor+" VALOR QUE REMPLAZA...");
if(p==raiz2)
p.izq = a.izq;
else
p.der = a.izq;
}

public void Eliminar(int elem) {
Nodo_vehiculos Padre = raiz;
Nodo_vehiculos aux = raiz;
boolean hijoizq = true;

boolean encontrado = false;
while(aux !=null) {
if(aux.valor == elem) {
encontrado = true;
if(aux==raiz) {
if(raiz.izq==null)
raiz = raiz.der;
else if(raiz.der==null)
raiz = raiz.izq;
else
Reemplazar(raiz);
}else {
System.out.println("Encontrado...");
if(aux.izq == null) {
if(hijoizq)
Padre.izq=aux.der;
else
Padre.der=aux.izq;
}else
Reemplazar(aux);

}
aux=null;
}else {
Padre =aux;
if(aux.valor > elem) {
aux=aux.izq;
hijoizq=true;
}else {
aux=aux.der;
hijoizq=false;
}
}
}


if(!encontrado)
System.out.println("El elemento no esxiste...");
}

public Arbol_raiz_carros (String color){ // polimorfirmos en la misma clase se denomina sebre carga de metodoso
    this.setColor(color);
}

public static void main (String[] args) {
    Scanner entrada = new Scanner(System.in);
    
    
    System.out.println("Ingrese Color de Vehiculo");
    String color  = entrada.nextLine();
    System.out.println("Ingrese Marca de Vehiculo que desea: "
    		+ "\\1. Chevrolet \\2. Renault \\3. Kia \\4. Suzuki");
    int tipoVehiculo  = entrada.nextInt();
    System.out.println("Ingrese días a alquilar:");
    System.out.println("");
    
Scanner leer = new Scanner(System.in);

Arbol_raiz_carros myArbol = new Arbol_raiz_carros();
int op, num, elim;
do {

System.out.println("Días a Incluir:  [1]");
System.out.println("Mostrar días incluidos: [2]");
System.out.println("Mostrar días incluidos de mayor a menor: [3]");
System.out.println("Eliminar días incluidos: [4]");
System.out.println("Salir [0]  : ");

op=leer.nextInt();
switch (op) {
case 1:  System.out.println("Ingrese días"); 
System.out.println(" ");
num = leer.nextInt();
myArbol.Insertar(num);
break;


case 2: myArbol.Preorden(myArbol.raiz);
       System.out.println("");
       break;

case 3: myArbol.Posorden(myArbol.raiz);
                System.out.println("");
                break;
case 4: System.out.println("Días a eliminar: ");
       elim = leer.nextInt();
       myArbol.Eliminar(elim);
       break;
 default: break;
 
}
}while(op != 0);


System.out.println("color: " + color );
System.out.println(" ");
System.out.println("Vehiculo Registrado");
System.out.println(" ");

}

public String getColor() {
	return color;
}

public void setColor(String color) {
	this.color = color;
}
}
