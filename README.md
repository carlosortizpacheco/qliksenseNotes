# qliksenseNotes

## Diferencial en porcentaje, filtrando por estado, por producto y por periodo anterior y actual 
(((sum({<Estado={'Distrito Federal','Estado de Mexico'},[SOutGroomenWDateTest (ec2amaz-sohujdk_joelmartinez).ProNombre]={"XXX 300"},[SOutGroomenWDateTest (ec2amaz-sohujdk_joelmartinez).semanaInicio]=[semanaInicio (ec2amaz-sohujdk_joelmartinez).semanaInicio]>}[SOutGroomenWDateTest (ec2amaz-sohujdk_joelmartinez).SOutMontoDesp])
/
count([semanaInicio (ec2amaz-sohujdk_joelmartinez).semanaInicio]))
/
(sum({<Estado={'Distrito Federal','Estado de Mexico'},[SOutGroomenWDateTest (ec2amaz-sohujdk_joelmartinez).ProNombre]={"XXX 300"},[SOutGroomenWDateTest (ec2amaz-sohujdk_joelmartinez).semanaFinal]=[semanaFinal (ec2amaz-sohujdk_joelmartinez).semanaFinal]>}[SOutGroomenWDateTest (ec2amaz-sohujdk_joelmartinez).SOutMontoDesp])
/
count([semanaFinal (ec2amaz-sohujdk_joelmartinez).semanaFinal])))
-1)


## Diff Monto Desp para tiendas que tienen y tiendas que no tienen PS
((Sum({<[Perf Store]={"0"}>}[SOutGroomenWDateTest (ec2amaz-sohujdk_joelmartinez).SOutMontoDesp])/
Sum({<[Perf Store]={"1"}>}[SOutGroomenWDateTest (ec2amaz-sohujdk_joelmartinez).SOutMontoDesp]))
-1)
*
100

## Dias de inventario (Inventario entre las sumatorias de las 4 semanas anteriores de Unid Desp

(
Sum([SOutUnidadesExis])
/
(
sum({<[SOutSemana]=([SOutSemana]-1)>}[SOutUnidadesDesp])
+
sum({<[SOutSemana]=([SOutSemana]-2)>}[SOutUnidadesDesp])
+
sum({<[SOutSemana]=([SOutSemana]-3)>}[SOutUnidadesDesp])
+
sum({<[SOutSemana]=([SOutSemana]-4)>}[SOutUnidadesDesp])
))
*
30

## Colocar el color que yo quiera en las tablas
if([ProID]='2581','#84BFB9',
if([ProID]='2582','#30BF8B','#25594B'))


## ordenar valores discretos 
if(DiaStr='lunes',1,if(DiaStr='martes',2,if(DiaStr='miércoles',3,if(DiaStr='jueves',4,if(DiaStr='viernes',5,if(DiaStr='sábado',6,if(DiaStr='domingo',7)))))))
