CIDR (Classless Inter-Domain Routing) é um método para a alocação de endereços IP e roteamento que melhora a eficiência do uso do espaço de endereçamento da Internet. Antes do CIDR, os endereços IP eram divididos rigidamente em classes A, B e C, que eram frequentemente inadequadas para o tamanho real das redes, levando ao desperdício de endereços. O CIDR elimina essas classes e permite a criação de sub-redes mais flexíveis e eficientes.

### Estrutura do CIDR

Um endereço CIDR é composto por um endereço IP, seguido de uma barra ("/") e um número que indica quantos bits na máscara de rede são fixos. Por exemplo:

```
192.168.1.0/24
```

Nesse exemplo, 192.168.1.0 é o endereço IP da rede, e /24 indica que os primeiros 24 bits do endereço são usados como a parte da rede, enquanto os últimos 8 bits (32 - 24 = 8) são usados para endereçamento de hosts dentro dessa rede. Isso equivale à máscara de sub-rede 255.255.255.0.

### Benefícios do CIDR

- **Maior Flexibilidade**: O CIDR permite definir sub-redes de tamanhos variados, proporcionando um uso mais eficiente dos endereços IP, em comparação com o sistema antigo de classes fixas.
- **Roteamento mais Simples**: Com o CIDR, várias sub-redes podem ser agregadas em uma única entrada de tabela de roteamento. Isso reduz a quantidade de entradas que os roteadores precisam armazenar, simplificando a manutenção da infraestrutura de rede.

### Exemplo de Notação CIDR

- /32: Um único endereço IP. Exemplo: 192.168.1.1/32 se refere apenas ao IP 192.168.1.1.
- /24: Representa uma rede com 256 endereços (de 192.168.1.0 a 192.168.1.255), dos quais 254 são utilizáveis (geralmente o primeiro endereço é reservado para a rede e o último para o broadcast).
- /16: Representa uma rede maior com 65.536 endereços (de 192.168.0.0 a 192.168.255.255).

### Cálculo do Número de Hosts

Para calcular o número de endereços disponíveis para hosts em uma rede CIDR, você usa a fórmula:

```
Número de hosts = 2^(32 - prefixo) - 2
```

O \-2 é necessário porque um endereço é reservado para a rede e outro para o broadcast. Por exemplo, para /24:

```
Número de hosts = 2^(32 - 24) - 2 = 256 - 2 = 254 hosts disponíveis
```

### Exemplos Práticos

- **192.168.0.0/23**: Esse CIDR abrange dois sub-redes de /24, ou seja, um total de 512 endereços IP (510 utilizáveis).
- **10.0.0.0/8**: Esse CIDR define uma grande rede com cerca de 16 milhões de endereços IP (usado frequentemente em grandes redes privadas).

### Conclusão

O CIDR é essencial para a eficiência do roteamento e uso do espaço de endereçamento IPv4. Ele é amplamente utilizado em redes modernas para criar sub-redes de tamanhos adequados, agregação de rotas e para evitar desperdício de endereços.

