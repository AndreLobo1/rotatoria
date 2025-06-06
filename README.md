### **Descrição do problema**

Simular computacionalmente o fluxo de veículos em uma rotatória com quatro vias de entrada e saída, respeitando regras de trânsito e analisando possíveis situações de conflito como o deadlock.

### **Abordagem de modelagem computacional**

Dividimos o sistema em entidades principais (carros, vias, rotatória e trechos), utilizando estruturas de dados adequadas para simular o comportamento dinâmico do tráfego.

### **Algoritmo proposto**

A cada tick de simulação, carros são inseridos nas vias, tentam entrar na rotatória se possível, percorrem os trechos e saem quando alcançam o destino, sempre respeitando regras de prioridade.

### **Exemplos ou simulações conceituais**

Um carro vindo do norte e indo para o leste entra na rotatória se o trecho estiver livre, circula até seu destino e sai. Se os quatro trechos estiverem ocupados por carros que se bloqueiam mutuamente, ocorre deadlock.

<div align="center">

![Simulação](https://www.plantuml.com/plantuml/svg/ZT6nJiCm4CRntK_nZUdG5o0ILE8Ls133ARaGIuulkhj6F0w8WOcfZ-0N8x5AwOBKpRR-idyd7yn9_JYbK1SXt3sIgg0R-PLGth54Gi_Wx4ezjI4EQ9wKkr6kZi7cvGCfBieFE_Z86Ot5QHU0yuMrH2QeE7avQQGsS396aykdN9SsSqqnnBH6WBdCWNCVXujlJJfHPOZ1AySGixDciJPKvTyWSWG9_A8sAjyz_GCrYkXlOD92kNmHPbB22j9oUelJxpCRUx-_n_CYoGcqEJhI5zp2FuzQnpwic-rxVW00)  

</div>

### **Modelagem com estrutura de dados**

**Entidades existentes:** Carro, Via, Rotatória, TrechoRotatória
**Estruturas adequadas:** Filas para vias de entrada, listas para trechos, enums para direção.

<div align="center">

![Diagrama de Classes](https://www.plantuml.com/plantuml/svg/ZLF1Rjim3BthAuXScdPmrm0z1KNH8FKXG9fqSRexOx4jLziA93aODlHhTXXstYVanoR9rXndEUmII-JZu-CJSsSiQbkNXJ1lN6rHOmbvWSPChDMygItDSbLb_8tWIbYs1S4zuuk38KY2gOUIWGGoBki2zp_tFvHFh9H5k_-j6OKuWtJnz909gkhILMlAKS5t0R1OhjQf-sPFS_SxJxDmMuRlkw-RpYTPbcRmk9ejfhF7oImJ8gXhsqcb0r6oOpGmXZaRU_EPyTR7j9UWDADBhEBP9JvmnJcZ7fwxn4wnz37wIdbjKQyvV-ibTgJvcNFKzuIoK6rserH1M8dtgCSrRPJ8ThvndDG7dxd0jB8QfHVpgQQQRgQejRhrBL0wFQf27KB3tFywMBWTIYbuGpgYpYEYqn2kZGgMBisLzMUb-ONAlY19nd9rfDAwqwkQs1eBbrY7My-uKkseRvlZeI-O8UlJjiJoO4xiyFUbZbe4CxPAKh1A3_-nyg25XrA07VlLGQBYa32TxgZkUCGJrkNr5gNgSIQzVa67iJZddQRXVmgCxfdeMvHr1gjqFfdEbel9GxfOBpCVwbOzLvNT_ohX6iA-4un0T_-p3ZSO3U0YIM1mFGYBEOwL9p3-6ns8IAqAz9rzRUpfLnWaGHxC53xbIvMdkBgyl1Z0j1spM_P04iAUvfLoWdOP2TeD54qwIMxZ8yEu1Nri8Hr9U0weIsZs22GUpjyn7R_hkAaC_aQydwpSAcCHjagtZ4PqHGSc7XDsXdhAzGanOAc4Ar0rZ1h7H9-YRzweCwy1tr4bwxBu0m00)

</div>

### **Lógica que define o movimento dos carros**

Cada carro tenta entrar na rotatória se o trecho de entrada estiver livre, avança a cada ciclo e sai ao alcançar o trecho correspondente ao destino.

### **Como funciona a tomada de decisão dos veículos**

Eles verificam se o próximo trecho está livre. Se sim, avançam; se não, esperam. Entram na rotatória apenas se o trecho de entrada estiver disponível.

### **Como representar prioridades e regras de trânsito**

A prioridade é dada a quem já está na rotatória. Carros só entram se não atrapalharem quem já está circulando.

### **Como seria um algoritmo para o processamento do fluxo de carros**

**Etapas básicas:**

1. Adicionar novos carros nas filas.
2. Verificar se podem entrar na rotatória.
3. Avançar os carros nos trechos.
4. Remover os que chegaram ao destino.

### **Como garantir que o algoritmo respeite as regras de preferência e evite conflitos**

Usando checagens antes de cada movimento e só permitindo entrada quando o trecho estiver livre e sem bloquear carros em circulação.

### **É possível haver uma situação onde nenhum carro consegue sair da rotatória?**

Sim. Isso acontece no deadlock, onde há um ciclo de espera circular entre os carros.

### **Sob quais condições ocorre um deadlock**

Quando quatro carros ocupam simultaneamente os quatro trechos da rotatória e cada um precisa que o próximo carro saia para poder avançar.

<div align="center">

![Deadlock](https://www.plantuml.com/plantuml/svg/NP0nJaCn38RtdC9ZktVg6re93i301KpYgX5976odS1t4m04umhiORka3L2c3zVjt_FdVgw7Og2LSYX2s6uWemWhKJB02LTY02SMZQochvMQiKzZUOS8VBtHlPqL8vtB-UikLhoFGKH3mX6t-H9b2o0TOFTnuI6r-1uwZO-BT6kn83LQQwpe0-1wHiwUJu1IeAC6gpH_yrrp-drnHunwefNm8GQWJcel_MKya-P0ZWjAufPsk8_1wpCNNF79Y1N_B_P6Rtp-mBhIwMtjcY-ytEZK7XAV2BuCmNUAwzw9mV8P4Hj5SzJGkj7l77RLy0m00)

</div>

### **Análise de deadlock e soluções**

Deadlock ocorre quando todos os trechos estão ocupados por carros que dependem uns dos outros para sair, sem que ninguém tenha prioridade clara.

### **Quais são os estados críticos que levam a isso?**

Quatro carros em sequência circular, cada um esperando pelo próximo, sem rota de saída disponível.

### **Como evitar o deadlock**

Implementando regras de prioridade para entrada e movimentação, limitando o número de carros na rotatória simultaneamente.

### **Que regras de prioridade poderiam ser adotadas**

Permitir entrada apenas se houver pelo menos dois trechos livres à frente, ou limitar a um carro por vez por direção, garantindo espaço para movimentação interna.
