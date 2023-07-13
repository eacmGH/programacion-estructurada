# TRABAJO PRACTICO NRO 3

## Dado un valor de 4 cifras ingresado por el usuario, determine si éste tiene todos sus dígitos distintos, es un valor capicúa, se compone sólo de dígitos impares o sólo tiene cifras pares. Tenga en cuenta que deben incluirse los controles para el correcto funcionamiento del algoritmo.

```
Algoritmo p6capikua_4cifras_mejorado
	Escribir "Ingrese numero de 4 cifras"
	Leer dato
	Si dato >= 1000 Y dato <= 9999 Entonces
		u <- dato mod 10
		d <- (trunc(dato / 10)) mod 10
		c <- trunc(trunc(dato / 10)/10) mod 10
		um <- trunc(trunc(trunc(dato / 10)/ 10)/10) mod 10
		distintos <- u <> d Y u <> c Y u <> um Y d <> c Y d <> um Y c <> um
		Si distintos Entonces
			Escribir "Todos sus digitos son distintos"
		SiNo
			Escribir "Sus digitos no son distintos"
		FinSi
		reverso <- (((0 * 10 + u ) * 10 + d ) * 10 + c) * 10 + um
		Si dato = reverso Entonces
			Escribir "Es capicua"
		SiNo
			Escribir "No es capicua"
		FinSi
		p <- u mod 2 = 0 Y d mod 2 = 0 Y c mod 2 = 0 Y um mod 2 = 0
		i <- u mod 2 <> 0 Y d mod 2 <> 0 Y c mod 2 <> 0 Y um mod 2 <> 0
		Si p Entonces
			Escribir "Todos sus digitos son pares"
		SiNo
			Si i Entonces
				Escribir "Todos sus digitos son impares"
			SiNo
				Escribir "No son pares ni impares"
			FinSi
		FinSi
	SiNo
		Escribir "Numero mayor o menor a 4 digitos"
	FinSi
FinAlgoritmo
```

## Ingresar un nombre de usuario, un servidor de correo (Gmail, Outlook, Yahoo!, etc.) y un dominio (ar, br, cl, etc.), y con éstos generar una dirección de correo electrónico. Tenga en cuenta que si alguno de los datos es nulo se omitirá la salida, presentándose un mensaje de advertencia al usuario.

```
Algoritmo p7validacion_email
	Escribir "Ingrese el nombre de usuario"
	Leer usuario
	usuarioNulo <- Longitud(usuario) = 0
	Escribir "Ingrese el proveedor de servicio de su correo electronico por ej. outlook, gmail, hotmail"
	Leer proveedor
	proveedorNulo <- Longitud(proveedor) = 0
	Escribir "Elija uno de los dominios del proveedor de servicio de su correo electronico. ar, br, es, mx, us"
	Leer dominio
	dominioNulo <- Longitud(dominio) = 0
	Si usuarioNulo O proveedorNulo O dominioNulo Entonces
		Escribir "Hay datos omitidos vuelvalo a intentar"
	SiNo
		Escribir usuario + "@" + proveedor + ".com." + dominio
	Fin Si
FinAlgoritmo
```

## Ingresar una cadena de caracteres y determinar si ésta está compuesta únicamente por letras mayúsculas. Considere que el algoritmo analizará cadenas de hasta 5 caracteres, presentando un mensaje de advertencia al usuario para aquellas que sean nulas o mayores 5 caracteres.

```
Algoritmo p8cad_caracteres_mejorado
	Escribir "Ingrese una cadena de hasta 5 caracteres"
	leer p
	valido <- Longitud(p) = 5 
	Si valido Entonces
		c1 <- Subcadena(p,1,1)
		c2 <- Subcadena(p,2,2)
		c3 <- Subcadena(p,3,3)
		c4 <- Subcadena(p,4,4)
		c5 <- Subcadena(p,5,5)
		mayus <- c1 >= 'A' Y c1 <= 'Z' Y c2 >= 'A' Y c2 <= 'Z' Y c3 >= 'A' Y c3 <= 'Z' Y c4 >= 'A' Y c4 <= 'Z' Y c5 >= 'A' Y c5 <= 'Z'
		Si mayus Entonces
			Escribir "Son todas mayusculas"
		SiNo
			Escribir "No son todas mayusculas"
		FinSi
	SiNo
		Si Longitud(p) = 0 Entonces
			Escribir "Es nula"
		SiNo
			Escribir "Mayor a 5 caracteres o menor"
		FinSi
	FinSi
FinAlgoritmo
```

## Ingresar un nombre de usuario y contraseña (4 caracteres) y validar que el nombre de usuario no inicie con un dígito y que la contraseña contenga al menos una letra mayúscula, una letra minúscula y un dígito. Si el nombre de usuario o la contraseña no son válidos deben presentarse los mensajes de error correspondientes.

```
Algoritmo p9user_pass4caracteres_mejorado
	Escribir "Ingrese nombre de usuario"
	Leer us
	usDig <- Subcadena(us,1,1)
	mayus <- Falso
	minus <- Falso
	digit <- Falso
	Si usDig >= '0' Y usDig <= '9' Entonces
		Escribir "Nombre invalido"
	SiNo
		Escribir "Nombre valido"
	FinSi
	Escribir "Ingrese contrasenia de 4 caracteres debe contener 1 mayuscula 1 minuscula y un digito"
	Leer pass
	Si Longitud(pass) = 4 Entonces
		L1<- Subcadena(pass,1,1)
		L2<- Subcadena(pass,2,2)
		L3<- Subcadena(pass,3,3)
		L4<- Subcadena(pass,4,4)
		mayus <- L1 >= 'A' Y L1 <= 'Z' O L2 >= 'A' Y L2 <= 'Z' O L3 >= 'A' Y L3 <= 'Z' O L4 >= 'A' Y L4 <= 'Z'
		minus <- L1 >= 'a' Y L1 <= 'z' O L2 >= 'a' Y L2 <= 'z' O L3 >= 'a' Y L3 <= 'z' O L4 >= 'a' Y L4 <= 'z'
		digit <- L1 >= '0' Y L1 <= '9' O L2 >= '0' Y L2 <= '9' O L3 >= '0' Y L3 <= '9' O L4 >= '0' Y L4 <= '9'
		Si mayus Y minus Y digit Entonces
			Escribir "Contrasenia correcta"
		SiNo
			Escribir "Contrasenia invalida"
		FinSi
	SiNo
		Escribir "Menos o mas de 4 caracteres"
	FinSi
	
FinAlgoritmo
```