                 |    1            p68H11                  declara el tipo de microprocesador.
                 |    2            ORG     $2000           declara la ubicacion del programa en memoria.
2000    8608     |    3            ldaa    #8              el numero de ciclos a realizar
2002    9760     |    4            staa    $60              se guarda en un contador en memoria.
2004    CE3000   |    5            ldx     #$3000          apunta X a la tabla de salida,
2007    4F       |    6            clra                     hace A:=0,
2008    4C       |    7            inca                     luego lo incrementa para tener A:=1,
2009    A700     |    8            staa    0,X              y almacena este valor en las dos
200B    A701     |    9            staa    1,X              primeras posiciones de la tabla de salida.
200D    A600     |   10    repite  ldaa    0,X             repetir: se toma un elemento en A
200F    E601     |   11            ldab    1,X              y el siguiente elemento en B;
2011    1B       |   12            aba                      se los suma y
2012    2508     |   13            bcs     sale               [siempre que no haya habido un error]
2014    A702     |   14            staa    2,X              se guarda el elemento sucesivo en la tabla.
2016    08       |   15            inx                     ahora avanza el puntero y
2017    7A0060   |   16            dec     $60              decrementa el contador,
201A    26F1     |   17            bne     repite           si no es cero, vuelve a repetir;
201C    4F       |   18    sale    clra
201D    A702     |   19            staa    2,X             graba una marca de terminacion y
201F    7E201F   |   20    fin     jmp     fin              queda "eternamente" aqui.
                 |   21            END
                 |   22    

