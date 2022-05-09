# Ingresos_regresion_lasso
En este proyecto analicé la importacia que existe entre diferentes variables que toma el inegi con relación al ingreso trimestral

En un primer proyecto que se encuentra en este [link](https://github.com/ervinflx/Ervin_Portafolio) se analizó la significancia que tenía la edad y la educación con el incremento de los ingresos trimestrales en México.
En este proyecto se realiza una regresión lasso con validación cruzada para identificar qué variables, de todas las que ENIGH 2016 ofrece, son importantes al momento de tener una relación significativa con el incremento de los ingresos trimestrales mexicanos.

Para la realizacón de esta identificación se realizó un preprocesamiento de los datos y se utilizaron las variables:
-ingreso trimestral
-sexo
-edad
-nivel de aprobación
-estado conyugal
-red social, la facilidad con la cual una persona puede conseguir ayuda para obtener un trabajo
-segsoc, contribuciones a la seguridad social
-trabajo_mp, distingue a la población de 12 o más años de acuerdo con el desempeño o no de una actividad económica en el periodo de referencia, permite clasificar al/la   menor como parte de la Población Económicamente Activa
-horas, número de horas que se trabajan 
-lengua, incluye lengua indigena, español o bilingüe
-discapacidad

```
ingreso %>% 
  sample_frac(0.2) -> ingreso_test
ingreso %>% 
  anti_join(ingreso_test) -> ingreso_train
```
Una vez seleccionados los diferentes grupos que voy a utilizar para el entrenamiento del modelo pongo a entrenar el primer conjunto.

| Variables | reducción de las variables por medio de lasso |
| ----------- | ----------- |
(Intercept)                                           7.34620632
sexoMujer                                            -0.30105839
edad                                                  0.01364039
nivelaprobSecundaria                                  0.20485057
nivelaprobPreparatoria o bachillerato                 0.46249455
nivelaprobTécnica/Normal                              0.67245068
nivelaprobProfesional                                 0.98504366
nivelaprobPosgrado                                    1.61803879
nivelaprobNinguno                                    -0.25270438
edo_conyugEs viudo(a)                                 0.20897234
edo_conyugEstá divorciado(a)                          0.19180292
edo_conyugEstá separado(a)                            0.09151752
edo_conyugEstá soltero(a)                            -0.28975900
edo_conyugVive con su pareja o en unión libre         .         
redsoc_3Difícil conseguirla                          -0.15806694
redsoc_3Fácil conseguirla                             0.02275194
redsoc_3Imposible conseguirla                        -0.18572554
redsoc_3Ni fácil ni difícil conseguirla (espontánea) -0.04836351
redsoc_3No aplica                                     0.39894748
segsocSí                                              0.61071821
trabajo_mpTrabajó el mes pasado                       0.57216288
hor_1                                                 0.01292444
lenguabilig                                          -0.24064179
lenguaind                                            -0.47228475
discSí                                               -0.18491723 
