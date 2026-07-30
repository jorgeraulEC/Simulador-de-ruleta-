# Simulador de ruleta

![Bash](https://img.shields.io/badge/Shell-Bash-4EAA25?style=flat-square&logo=gnu-bash&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)
![Platform](https://img.shields.io/badge/Platform-Linux-yellow?style=flat-square)
 
Simulador de terminal que pone a prueba dos sistemas clásicos de apuestas en la ruleta —**Martingala** y **Labouchere Inversa**— apostando siempre a par/impar con dinero ficticio.

![demo](docs/demo.gif)
 
##  Características
 
- Simulación de ruleta europea (0–36) con `RANDOM`
-  Estrategia **Martingala**: duplica la apuesta tras cada pérdida
- Estrategia **Labouchere Inversa**: secuencia dinámica que crece al ganar y se reduce al perder
- Resumen de sesión al finalizar (rondas jugadas, ganadas, perdidas, balance)
-  Detección automática de bancarrota / fin de secuencia

  
## Requisitos
 
- `bash` (4.3+, por el uso de índices negativos en arrays)
- `tput` (incluido normalmente en `ncurses`)
No requiere dependencias externas ni conexión a internet.
 
##  Instalación
 
```bash
git clone https://github.com/tu-usuario/roulette-strategy-simulator.git
cd roulette-strategy-simulator
chmod +x ruleta.sh
```
 
### Instalación global (opcional)
 
```bash
./install.sh
```
 
##  Uso
 
```bash
./ruleta.sh -m <saldo_inicial> -t <tecnica>
```
 
| Flag | Descripción | Ejemplo |
|------|-------------|---------|
| `-m <cantidad>` | Bankroll / saldo inicial | `-m 500` |
| `-t <tecnica>` | Técnica a usar: `martingala` o `inverseLabrouchere` | `-t martingala` |
| `-h` | Mostrar panel de ayuda | `-h` |
 
### Ejemplos
 
```bash
# Simular Martingala con 500 de saldo inicial
./ruleta.sh -m 500 -t martingala
 
# Simular Labouchere Inversa con 300 de saldo inicial
./ruleta.sh -m 300 -t inverseLabrouchere
```
 
Durante la ejecución se te pedirá la apuesta inicial (Martingala) y a qué color/paridad apostar. El script corre en bucle hasta que te quedas sin saldo suficiente o interrumpes con `Ctrl+C`.
 
##  ¿Por qué pierden ambas técnicas?
 
- **Martingala**: en teoría "recuperas todo" al duplicar tras cada pérdida, pero requiere bankroll infinito. En la práctica, una racha de pérdidas consecutivas (más probable de lo que parece) te deja sin saldo suficiente para seguir duplicando, o topas con el límite de mesa.
- **Labouchere Inversa**: ajusta el tamaño de apuesta según una secuencia, pero al igual que Martingala, no cambia la probabilidad real de cada tirada (18/37 ≈ 48.6% en par/impar). El cero garantiza una ventaja estructural a favor de la casa que ningún sistema de gestión de apuestas puede eliminar.
Este proyecto es una demostración práctica de por qué los "sistemas infalibles" de ruleta no funcionan matemáticamente.
 

##  Licencia
 
Distribuido bajo la licencia MIT. Consulta [LICENSE](LICENSE) para más información.
