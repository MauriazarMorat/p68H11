                 |    1        p68H11
                 |    2        ORG $2000
2000    8611     |    3        ldaa    #00010001b   ponemos el bit 
2002    973C     |    4        staa    %60 lo guardo en el 60
2004    4F       |    5        clra        se cleariza a
2005    8607     |    6        ldaa    #7
2007    9740     |    7        staa    %64 guardamos la cantidad de bucle
2009    4F       |    8        clra
200A    C601     |    9        ldab    #00000001b   ponemos la mask
200C    CE3000   |   10        ldx     #$3000
200F    E701     |   11        stab    1,X
2011    963C     |   12    bucle       ldaa    %60 buscamos el valor de A
2013    A401     |   13        anda    1,X hacemos and con la mascara
2015    2602     |   14        bne     ifuno   saltamos si hay 1 en el bit
2017    2002     |   15        bra     sigue   entonces seguimos
2019    1808     |   16    ifuno       iny     sumamos 1 al contador
201B    58       |   17    sigue       lslb    movemos la mask un bit
201C    08       |   18        inx             sumamos uno al pointer
201D    E701     |   19        stab    1,X     ponemos el siguiente BIT de la mask
201F    7A0040   |   20        dec     %64     decrementamos el contador
2022    26ED     |   21        bne     bucle   si terminamos saltamos    
2024    7E2024   |   22    fin jmp     fin
                 |   23        END

