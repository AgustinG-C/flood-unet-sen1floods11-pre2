# Resultados de la corrida reportada (una semilla, 1500 pasos por configuración, 1500 chips débiles)

## Ablación (clase agua, umbral 0.5)
| Config. | IoU val | IoU test | F1 test | Prec. test | Recall test | IoU Bolivia |
|---|---|---|---|---|---|---|
| A1 dorada, BCE+Dice | 0.630 | 0.676 | 0.807 | 0.822 | 0.791 | 0.639 |
| A2 dorada + débil (mezcla) | 0.585 | 0.628 | 0.772 | 0.792 | 0.753 | 0.696 |
| A3 débil -> ajuste fino | 0.629 | 0.657 | 0.793 | 0.824 | 0.765 | 0.594 |
| B1 BCE | 0.611 | 0.649 | 0.787 | 0.851 | 0.733 | 0.547 |
| B2 Dice | 0.630 | 0.675 | 0.806 | 0.819 | 0.793 | 0.611 |
| C1 profundidad 3 | 0.623 | 0.668 | 0.801 | 0.817 | 0.785 | 0.584 |
| C2 Attention U-Net | 0.631 | 0.670 | 0.803 | 0.839 | 0.769 | 0.528 |
| C3 sin saltos | 0.595 | 0.622 | 0.767 | 0.773 | 0.761 | 0.640 |

## Modelo final (C2, umbral 0.25 calibrado en validación)
| | IoU | IoU/chip | F1 | Precisión | Recall |
|---|---|---|---|---|---|
| Test (eventos vistos) | 0.6704 | 0.4099 | 0.8027 | 0.7954 | 0.8100 |
| Bolivia (no visto) | 0.5926 | 0.3709 | 0.7442 | 0.8537 | 0.6595 |

## Bono (chips sin nubes)
| Modelo | IoU val | IoU test | IoU Bolivia |
|---|---|---|---|
| Solo SAR | 0.664 | 0.627 | 0.782 |
| SAR + S2 | 0.859 | 0.865 | 0.894 |

Los CSV y figuras originales se generan en `/content/outputs` al ejecutar el notebook
(`ablacion_resultados.csv`, `brecha_bolivia.csv`, `bono_fusion.csv`, `modelo_final.pt`, figuras).
Descárguelos desde Colab y colóquelos en esta carpeta antes de hacer el commit.
