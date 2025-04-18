# Simulação de Algoritmo de Leilão em Fog Federada
Implementação de uma simulação de algoritmos de leilão aplicados em ambientes de computação em névoa com federação entre domínios. O objetivo é avaliar estratégias de alocação de recursos otimizadas por meio de leilões entre diferentes nós fog, promovendo eficiência e colaboração em cenários distribuídos.

### Cálculo da Tabela de Benefícios
- Cada requisição possui uma latência máxima desejada e um uplink mínimo desejado
- Cada fog possui um valor de latência e um uplink


O cálculo da benefício requisição x fog é feito da seguinte forma:

```py
diferença_latência = latência_request - latência_fog
diferença_uplink = uplink_fog - uplink_request

benefício = diferença_latência + diferença_uplink
```

Veja que o valor do benefício pode ser negativo, o que não é permitido no algoritmo de leilão. Dessa forma, caso haja valor negativo, é feita uma correção na tabela de benefícios onde cada valor da tabela é somado ao módulo do menor valor negativo de benefício.


## Formas de obter as métricas necessárias

- **Latência**: é possível medir latência utilizando um ping básico
- **Tempo de Resposta**: Latência + Tempo de processamento -> Ideia: a cada requisição processada pela fog, calcular o tempo de resposta e gerar uma média móvel.

