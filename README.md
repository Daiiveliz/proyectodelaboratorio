Algoritmo SistemaIndumentariaPro
	
	// ============================================================================
	// DECLARACIÓN DE VECTORES Y VARIABLES GLOBALES
	// ============================================================================
	
	// 1. Vector de Usuarios (Máximo 100 registros)
	Definir idUsuario como Entero
	Definir dniUsuario, nombreUsuario, apellidoUsuario, telUsuario, dirUsuario como Caracter
	Definir rolUsuario como Entero
	Dimension idUsuario[100], dniUsuario[100], nombreUsuario[100], apellidoUsuario[100], telUsuario[100], dirUsuario[100], rolUsuario[100]
	Definir cantUsuarios como Entero
	cantUsuarios <- 0
	
	// 2. Vector de Proveedores (Máximo 50 registros)[cite: 3]
	Definir idProv como Entero
	Definir razonSocialProv, origenProv, especialidadProv como Caracter
	Dimension idProv[50], razonSocialProv[50], origenProv[50], especialidadProv[50]
	Definir cantProv como Entero
	cantProv <- 0
	
	// 3. Vector de Prendas / Inventario (Máximo 100 registros)[cite: 3]
	Definir codPrenda, nombrePrenda, catPrenda como Caracter
	Definir precioPrenda como Real
	Definir stockSPrenda, stockMPrenda, stockLPrenda, idProvPrenda como Entero
	Dimension codPrenda[100], nombrePrenda[100], catPrenda[100], precioPrenda[100], stockSPrenda[100], stockMPrenda[100], stockLPrenda[100], idProvPrenda[100]
	Definir cantPrendas como Entero
	cantPrendas <- 0
	
	// 4. Variables de Caja (Caja Z y control de recaudación diaria)[cite: 3]
	Definir cajaTotal, cajaEfectivo, cajaTarjeta como Real
	Definir totalFacturas como Entero
	cajaTotal <- 0.0
	cajaEfectivo <- 0.0
	cajaTarjeta <- 0.0
	totalFacturas <- 0
	
	// ============================================================================
	// PRECARGA DE DATOS INICIALES (Simula base de datos base)
	// ============================================================================
	
	// Precarga de Usuarios[cite: 3]
	idUsuario[0] <- 1; dniUsuario[0] <- "11111111"; nombreUsuario[0] <- "Carlos"; apellidoUsuario[0] <- "Gomez"; telUsuario[0] <- "11-4444-5555"; dirUsuario[0] <- "Av. Corrientes 100"; rolUsuario[0] <- 1
	idUsuario[1] <- 2; dniUsuario[1] <- "22222222"; nombreUsuario[1] <- "Laura"; apellidoUsuario[1] <- "Perez"; telUsuario[1] <- "11-6666-7777"; dirUsuario[1] <- "Calle Falsa 123"; rolUsuario[1] <- 2
	idUsuario[2] <- 3; dniUsuario[2] <- "33333333"; nombreUsuario[2] <- "Textil"; apellidoUsuario[2] <- "Sur"; telUsuario[2] <- "11-8888-9999"; dirUsuario[2] <- "Ruta 8 Km 40"; rolUsuario[2] <- 3
	idUsuario[3] <- 4; dniUsuario[3] <- "44444444"; nombreUsuario[3] <- "Maria"; apellidoUsuario[3] <- "Lopez"; telUsuario[3] <- "11-2222-3333"; dirUsuario[3] <- "San Martin 450"; rolUsuario[4] <- 4
	cantUsuarios <- 4
	
	// Precarga de Proveedores[cite: 3]
	idProv[0] <- 101; razonSocialProv[0] <- "Textil Sur SRL"; origenProv[0] <- "Nacional"; especialidadProv[0] <- "Remeras y Jeans"
	idProv[1] <- 102; razonSocialProv[1] <- "Importadora Global"; origenProv[1] <- "Extranjero"; especialidadProv[1] <- "Camperas y Sacos"
	cantProv <- 2
	
	// Precarga de Prendas[cite: 3]
	codPrenda[0] <- "RE01"; nombrePrenda[0] <- "Remera Oversize"; catPrenda[0] <- "Remeras"; precioPrenda[0] <- 15000.0; stockSPrenda[0] <- 2; stockMPrenda[0] <- 5; stockLPrenda[0] <- 10; idProvPrenda[0] <- 101
	codPrenda[1] <- "PA01"; nombrePrenda[1] <- "Pantalon Cargo"; catPrenda[1] <- "Pantalones"; precioPrenda[1] <- 32000.0; stockSPrenda[1] <- 8; stockMPrenda[1] <- 12; stockLPrenda[1] <- 4; idProvPrenda[1] <- 102
	cantPrendas <- 2
	
	// ============================================================================
	// MENÚ PRINCIPAL INTERACTIVO (Bucle General del Sistema)
	// ============================================================================
	Definir opcionPrincipal como Entero
	Repetir
		Limpiar Pantalla
		Escribir "===================================================================="
		Escribir "                 SISTEMA DE GESTION Y STOCK v2.0                    "
		Escribir "===================================================================="
		Escribir "                       [ MENU PRINCIPAL ]                           "
		Escribir "--------------------------------------------------------------------"
		Escribir "  1. Ingresar como ADMINISTRADOR"
		Escribir "  2. Ingresar como REPOSITOR"
		Escribir "  3. Ingresar como PROVEEDOR"
		Escribir "  4. Ingresar como CLIENTE / VENTAS"
		Escribir "  5. Salir del Sistema"
		Escribir "--------------------------------------------------------------------"
		Escribir Sin Saltar "  > Seleccione una opcion: "
		Leer opcionPrincipal
		
		Segun opcionPrincipal Hacer
			
				// --------------------------------------------------------------------
				// OPCIÓN 1: PANEL ADMINISTRATIVO (CRUD de Usuarios, Proveedores y Prendas)
				// --------------------------------------------------------------------
			1:
				Definir opcAdmin como Entero
				Repetir
					Limpiar Pantalla
					Escribir "                      [ PANEL ADMINISTRATIVO ]                      "
					Escribir "--------------------------------------------------------------------"
					Escribir "  1. Registrar Nuevo Usuario"
					Escribir "  2. Listar Todos los Usuarios"
					Escribir "  3. Registrar Nuevo Proveedor"
					Escribir "  4. Cargar Nueva Prenda al Inventario"
					Escribir "  5. Ejecutar Cierre Fiscal (Caja Z)"
					Escribir "  6. Volver al Menú Principal"
					Escribir "--------------------------------------------------------------------"
					Escribir Sin Saltar "  > Seleccione una opción: "
					Leer opcAdmin
					
					Segun opcAdmin Hacer
						1: // Alta de nuevo usuario guardando en la posición del vector
							Si cantUsuarios < 100 Entonces
								idUsuario[cantUsuarios] <- cantUsuarios + 1
								Escribir "  > ID Asignado: #", idUsuario[cantUsuarios]
								Escribir Sin Saltar "  > Ingrese DNI: "; Leer dniUsuario[cantUsuarios]
								Escribir Sin Saltar "  > Ingrese Nombre: "; Leer nombreUsuario[cantUsuarios]
								Escribir Sin Saltar "  > Ingrese Apellido: "; Leer apellidoUsuario[cantUsuarios]
								Escribir Sin Saltar "  > Ingrese Telefono: "; Leer telUsuario[cantUsuarios]
								Escribir Sin Saltar "  > Ingrese Dirección: "; Leer dirUsuario[cantUsuarios]
								Repetir
									Escribir "  > Perfil (1: Admin, 2: Repositor, 3: Proveedor, 4: Cliente): "
									Leer rolUsuario[cantUsuarios]
								Hasta Que rolUsuario[cantUsuarios] >= 1 Y rolUsuario[cantUsuarios] <= 4
								cantUsuarios <- cantUsuarios + 1
								Escribir "  [?] ¡Usuario registrado con éxito!"
							Sino
								Escribir "  [!] Límite de usuarios alcanzado."
							FinSi
							Esperar Tecla
							
						2: // Listar usuarios recorriendo el vector
							Limpiar Pantalla
							Escribir "                       [ NOMINA DE USUARIOS ]                       "
							Escribir "--------------------------------------------------------------------"
							Para i <- 0 Hasta cantUsuarios - 1 Con Paso 1 Hacer
								Escribir "ID: ", idUsuario[i], " | DNI: ", dniUsuario[i], " | Nombre: ", nombreUsuario[i], " ", apellidoUsuario[i], " | Rol: ", rolUsuario[i]
							FinPara
							Escribir "--------------------------------------------------------------------"
							Esperar Tecla
							
						3: // Registrar Proveedor en vectores paralelos[cite: 3]
							Si cantProv < 50 Entonces
								Escribir Sin Saltar "  > Ingrese ID Único de Proveedor: "; Leer idProv[cantProv]
								Escribir Sin Saltar "  > Ingrese Razón Social: "; Leer razonSocialProv[cantProv]
								Definir opcOri como Entero
								Escribir Sin Saltar "  > Origen (1: Nacional, 2: Extranjero): "; Leer opcOri
								Si opcOri = 1 Entonces
									origenProv[cantProv] <- "Nacional"
								Sino
									origenProv[cantProv] <- "Extranjero"
								FinSi
								Escribir Sin Saltar "  > Especialidad: "; Leer especialidadProv[cantProv]
								cantProv <- cantProv + 1
								Escribir "  [?] ¡Proveedor registrado con éxito!"
							Sino
								Escribir "  [!] Base de proveedores llena."
							FinSi
							Esperar Tecla
							
						4: // Cargar nueva prenda validando datos positivos[cite: 3]
							Si cantPrendas < 100 Entonces
								Escribir Sin Saltar "  > Código del Producto: "; Leer codPrenda[cantPrendas]
								Escribir Sin Saltar "  > Nombre / Descripción: "; Leer nombrePrenda[cantPrendas]
								Escribir Sin Saltar "  > Categoría: "; Leer catPrenda[cantPrendas]
								Repetir
									Escribir Sin Saltar "  > Precio Unitario ($): "; Leer precioPrenda[cantPrendas]
									Si precioPrenda[cantPrendas] <= 0 Entonces
										Escribir "    [!] El precio debe ser mayor a 0."
									FinSi
								Hasta Que precioPrenda[cantPrendas] > 0
								Escribir Sin Saltar "  > Stock Talle S: "; Leer stockSPrenda[cantPrendas]
								Escribir Sin Saltar "  > Stock Talle M: "; Leer stockMPrenda[cantPrendas]
								Escribir Sin Saltar "  > Stock Talle L: "; Leer stockLPrenda[cantPrendas]
								Escribir Sin Saltar "  > ID de Proveedor Asignado: "; Leer idProvPrenda[cantPrendas]
								cantPrendas <- cantPrendas + 1
								Escribir "  [?] ¡Prenda cargada correctamente!"
							Sino
								Escribir "  [!] Catálogo lleno."
							FinSi
							Esperar Tecla
							
						5: // Informe de Caja Z y reseteo diario[cite: 3]
							Limpiar Pantalla
							Escribir "                 [ INFORME DIARIO - CAJA Z ]                        "
							Escribir "--------------------------------------------------------------------"
							Escribir "  > Total Facturas Emitidas: ", totalFacturas
							Escribir "  > Recaudación en Efectivo: $", cajaEfectivo
							Escribir "  > Recaudación en Tarjeta: $", cajaTarjeta
							Escribir "--------------------------------------------------------------------"
							Escribir "  TOTAL GENERAL RECAUDADO: $", cajaTotal
							Escribir "--------------------------------------------------------------------"
							Escribir "  [?] Caja reiniciada a $0.00"
							cajaTotal <- 0.0
							cajaEfectivo <- 0.0
							cajaTarjeta <- 0.0
							totalFacturas <- 0
							Esperar Tecla
					FinSegun
				Hasta Que opcAdmin = 6
				
				// --------------------------------------------------------------------
				// OPCIÓN 2: PANEL DE REPOSITOR (Control de inventario y stock crítico)
				// --------------------------------------------------------------------
			2:
				Definir opcRepo como Entero
				Repetir
					Limpiar Pantalla
					Escribir "                       [ PANEL DE REPOSITOR ]                       "
					Escribir "--------------------------------------------------------------------"
					Escribir "  1. Ver Stock General por Talle"
					Escribir "  2. Ver Alertas de Stock Crítico (< 3 unidades)"
					Escribir "  3. Volver al Menú Principal"
					Escribir "--------------------------------------------------------------------"
					Escribir Sin Saltar "  > Seleccione una opción: "
					Leer opcRepo
					
					Segun opcRepo Hacer
						1: // Muestra el catálogo de prendas y stock recorriendo vectores
							Limpiar Pantalla
							Escribir "                 [ CATALOGO DE PRODUCTOS Y STOCK ]                  "
							Escribir "--------------------------------------------------------------------"
							Para i <- 0 Hasta cantPrendas - 1 Con Paso 1 Hacer
								Escribir "Cod: ", codPrenda[i], " | ", nombrePrenda[i], " | Precio: $", precioPrenda[i]
								Escribir "      Stock -> S: ", stockSPrenda[i], " | M: ", stockMPrenda[i], " | L: ", stockLPrenda[i]
								Escribir "------------------------------------------------------------------"
							FinPara
							Esperar Tecla
							
						2: // Alerta de stock crítico menor a 3 unidades[cite: 3]
							Limpiar Pantalla
							Escribir "           [ ALERTAS DE REPOSICIÓN - STOCK CRITICO ]                "
							Escribir "--------------------------------------------------------------------"
							Definir hayAlerta como Logico
							hayAlerta <- Falso
							Para i <- 0 Hasta cantPrendas - 1 Con Paso 1 Hacer
								Si stockSPrenda[i] < 3 O stockMPrenda[i] < 3 O stockLPrenda[i] < 3 Entonces
									Escribir "  [!] REPOSICIÓN REQUERIDA -> Prenda: ", nombrePrenda[i], " (Cód: ", codPrenda[i], ")"
									Escribir "      Stock -> S: ", stockSPrenda[i], " | M: ", stockMPrenda[i], " | L: ", stockLPrenda[i]
									hayAlerta <- Verdadero
								FinSi
							FinPara
							Si NO hayAlerta Entonces
								Escribir "  [?] Todo el inventario cuenta con stock óptimo (>= 3 unidades)."
							FinSi
							Esperar Tecla
					FinSegun
				Hasta Que opcRepo = 3
				
				// --------------------------------------------------------------------
				// OPCIÓN 3: ACCESO A PROVEEDORES (Consulta de productos propios)[cite: 3]
				// --------------------------------------------------------------------
			3:
				Limpiar Pantalla
				Escribir "                      [ ACCESO A PROVEEDORES ]                      "
				Escribir "--------------------------------------------------------------------"
				Definir idIngresado como Entero
				Escribir Sin Saltar "  > Ingrese su ID de Proveedor: "; Leer idIngresado
				Escribir "--------------------------------------------------------------------"
				Definir encontroProv como Logico
				encontroProv <- Falso
				Para i <- 0 Hasta cantPrendas - 1 Con Paso 1 Hacer
					Si idProvPrenda[i] = idIngresado Entonces
						Escribir "  ? ", nombrePrenda[i], " | Stock -> S: ", stockSPrenda[i], " | M: ", stockMPrenda[i], " | L: ", stockLPrenda[i]
						encontroProv <- Verdadero
					FinSi
				FinPara
				Si NO encontroProv Entonces
					Escribir "  [!] No se encontraron productos vinculados a su ID."
				FinSi
				Esperar Tecla
				
				// --------------------------------------------------------------------
				// OPCIÓN 4: CLIENTE Y VENTAS (Facturación, descuento y descuento de stock)[cite: 3]
				// --------------------------------------------------------------------
			4:
				Definir opcCliente como Entero
				Repetir
					Limpiar Pantalla
					Escribir "                      [ CATALOGO Y ATENCIÓN ]                       "
					Escribir "--------------------------------------------------------------------"
					Escribir "  1. Consultar Productos y Precios"
					Escribir "  2. Realizar Compra de Producto"
					Escribir "  3. Volver al Menú Principal"
					Escribir "--------------------------------------------------------------------"
					Escribir Sin Saltar "  > Seleccione una opcion: "
					Leer opcCliente
					
					Segun opcCliente Hacer
						1: // Listar productos
							Limpiar Pantalla
							Escribir "                 [ CATALOGO DE PRODUCTOS Y STOCK ]                  "
							Escribir "--------------------------------------------------------------------"
							Para i <- 0 Hasta cantPrendas - 1 Con Paso 1 Hacer
								Escribir "Cod: ", codPrenda[i], " | ", nombrePrenda[i], " | Precio: $", precioPrenda[i]
								Escribir "      Stock -> S: ", stockSPrenda[i], " | M: ", stockMPrenda[i], " | L: ", stockLPrenda[i]
								Escribir "------------------------------------------------------------------"
							FinPara
							Esperar Tecla
							
						2: // Proceso de venta, validación de talles y actualización de caja[cite: 3]
							Limpiar Pantalla
							Escribir "                     [ MODULO DE VENTAS ]                           "
							Escribir "--------------------------------------------------------------------"
							Definir codigoBuscado como Caracter
							Escribir Sin Saltar "  > Ingrese Código del Producto: "; Leer codigoBuscado
							
							Definir posEncontrada como Entero
							posEncontrada <- -1
							Para i <- 0 Hasta cantPrendas - 1 Con Paso 1 Hacer
								Si codPrenda[i] = codigoBuscado Entonces
									posEncontrada <- i
								FinSi
							FinPara
							
							Si posEncontrada = -1 Entonces
								Escribir "  [!] Error: Código de producto no encontrado."
							Sino
								Definir talleReq como Caracter
								Escribir "  > Producto: ", nombrePrenda[posEncontrada]
								Escribir Sin Saltar "  > Ingrese Talle Requerido (S, M, L): "; Leer talleReq
								
								Definir stockDisp como Entero
								stockDisp <- 0
								Si talleReq = "S" O talleReq = "s" Entonces
									stockDisp <- stockSPrenda[posEncontrada]
								Sino
									Si talleReq = "M" O talleReq = "m" Entonces
										stockDisp <- stockMPrenda[posEncontrada]
									Sino
										Si talleReq = "L" O talleReq = "l" Entonces
											stockDisp <- stockLPrenda[posEncontrada]
										FinSi
									FinSi
								FinSi
								
								Escribir "  > Stock Disponible: ", stockDisp
								Definir cantComprar como Entero
								Escribir Sin Saltar "  > Cantidad a Comprar: "; Leer cantComprar
								
								Si cantComprar > 0 Y cantComprar <= stockDisp Entonces
									Definir nombreCliente como Caracter
									Definir tipoComprobante como Caracter
									Definir medioPago como Entero
									
									Escribir Sin Saltar "  > Nombre del Cliente: "; Leer nombreCliente
									Escribir Sin Saltar "  > Tipo de Comprobante (A, B, C): "; Leer tipoComprobante
									Escribir Sin Saltar "  > Medio de Pago (1: Efectivo 10% desc., 2: Tarjeta): "; Leer medioPago
									
									Definir subtotal, totalFinal como Real
									subtotal <- precioPrenda[posEncontrada] * cantComprar
									
									// Aplicar descuento por pago en efectivo
									Si medioPago = 1 Entonces
										totalFinal <- subtotal * 0.90
										cajaEfectivo <- cajaEfectivo + totalFinal
									Sino
										totalFinal <- subtotal
										cajaTarjeta <- cajaTarjeta + totalFinal
									FinSi
									
									// Descontar las unidades compradas del vector de stock correspondiente
									Si talleReq = "S" O talleReq = "s" Entonces
										stockSPrenda[posEncontrada] <- stockSPrenda[posEncontrada] - cantComprar
									Sino
										Si talleReq = "M" O talleReq = "m" Entonces
											stockMPrenda[posEncontrada] <- stockMPrenda[posEncontrada] - cantComprar
										Sino
											stockLPrenda[posEncontrada] <- stockLPrenda[posEncontrada] - cantComprar
										FinSi
									FinSi
									
									cajaTotal <- cajaTotal + totalFinal
									totalFacturas <- totalFacturas + 1
									
									// Generación e impresión de la Factura de compra[cite: 3]
									Limpiar Pantalla
									Escribir "                     =======================                        "
									Escribir "                     |  FACTURA TIPO ", tipoComprobante, "  |                        "
									Escribir "                     =======================                        "
									Escribir "  Cliente: ", nombreCliente
									Escribir "  Detalle: ", cantComprar, " unidad(es) x ", nombrePrenda[posEncontrada]
									Escribir "  ------------------------------------------------------------------"
									Escribir "  TOTAL A PAGAR: $", totalFinal
									Escribir "  ------------------------------------------------------------------"
									Escribir "                   ¡Gracias por su compra!                          "
								Sino
									Escribir "  [!] Cantidad no válida o stock insuficiente."
								FinSi
							FinSi
							Esperar Tecla
					FinSegun
				Hasta Que opcCliente = 3
				
			5: // Salir del programa
				Limpiar Pantalla
				Escribir "  [?] Sistema finalizado correctamente. ¡Gracias por usar Indumentaria Pro!"
		FinSegun
	Hasta Que opcionPrincipal = 5
	
FinAlgoritmo
