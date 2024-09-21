![Diseño sin título](https://github.com/user-attachments/assets/d685c71e-27e0-4bc8-a319-f627c94c4bcc)# Ciclo-de-Relaci-n-de-Clientes
Reactivados = 
CALCULATE (
    COUNTROWS(Tabla2),
    FILTER (
        Tabla2,
        (Tabla2[Valor] = "1.ACTIVO") &&   -- Estado ACTIVO
        (Tabla2[Fecha] = EDATE(SELECTEDVALUE(Tabla1[Atributo]), 1)) &&   -- Fecha en el mes siguiente al rango seleccionado
        (Tabla2[cedula] IN 
            CALCULATETABLE(
                VALUES(Tabla1[CEDULA]),  -- Utilizar Tabla1 para obtener las cédulas que cumplen ciertas condiciones
                FILTER (
                    Tabla1,
                    Tabla1[Valor] IN {"2.INACTIVO", "3.DESERTOR", "4.EXCLIENTE"}   -- Estados INACTIVO, DESERTOR, EXCLIENTE
                )
            )
        )
    )
)
![Ecuación de Clientes](https://github.com/user-attachments/assets/86c243d3-b785-4067-a3fa-a662ed025399)

