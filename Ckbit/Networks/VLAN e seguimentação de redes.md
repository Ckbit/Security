---
folder: "[[Networks]]"
---
VLANs (Virtual Local Area Networks) e segmentação de rede são conceitos usados para melhorar a segurança, o desempenho e a gestão de redes de computadores, especialmente em ambientes corporativos.

### VLANs (Virtual Local Area Networks)

Uma VLAN é uma rede local virtual que permite criar redes lógicas independentes dentro de uma rede física. Ou seja, uma única infraestrutura de rede física pode ser dividida em múltiplas redes virtuais, que funcionam de maneira independente umas das outras.

Imagine um prédio de uma empresa com diferentes departamentos, como RH, Finanças e TI. Em vez de construir uma rede física separada para cada departamento, você pode usar VLANs para segmentar logicamente esses departamentos, mesmo que todos os computadores estejam conectados aos mesmos switches e roteadores. Cada VLAN funcionará como se fosse uma rede separada, garantindo que o tráfego da rede de RH, por exemplo, não possa ser acessado por Finanças sem permissões adequadas.

### Benefícios das VLANs

1. **Segurança**: VLANs ajudam a isolar diferentes grupos de usuários e dispositivos, limitando o acesso aos recursos da rede. Isso impede que dispositivos em diferentes VLANs se comuniquem diretamente, a menos que exista uma configuração específica, aumentando a segurança.
2. **Eficiência e Gestão**: Permitir que dispositivos em áreas diferentes, mas com a mesma função, sejam agrupados facilita o gerenciamento de redes. Se um novo dispositivo for adicionado, ele apenas precisa ser configurado para a VLAN correta.
3. **Desempenho**: Ao segmentar a rede, é possível reduzir o domínio de broadcast (área onde o tráfego de broadcast se propaga). Isso melhora a eficiência da rede, pois reduz o número de dispositivos que recebem pacotes que não são relevantes para eles.

### Segmentação de Rede

Segmentação de rede refere-se ao ato de dividir uma rede em várias partes menores para melhorar a segurança e o desempenho. Pode ser feita usando VLANs ou outras técnicas, como sub-redes.

Na segmentação, a rede é subdividida em "segmentos", que podem ser isolados de outras partes da rede para reduzir o impacto de problemas de segurança ou desempenho. A segmentação permite definir regras de acesso que controlam o que pode ser acessado entre os segmentos, ajudando a proteger dados sensíveis e a minimizar o tráfego desnecessário.

### Exemplos de Aplicação

- **Segurança**: Se você segmenta uma rede, pode manter dispositivos como servidores, usuários de TI e usuários comuns em segmentos separados. Isso faz com que a segurança seja aumentada, pois mesmo que uma área da rede seja comprometida, as outras continuam protegidas.
- **Controle de Broadcast**: Como mencionado, em redes maiores, o tráfego de broadcast pode consumir uma quantidade significativa de largura de banda. A segmentação, seja através de VLANs ou sub-redes, ajuda a limitar a propagação desse tipo de tráfego.

Em resumo, VLANs são uma forma prática de segmentação de rede, usada para criar sub-redes lógicas que melhoram a segurança e o desempenho dentro de uma infraestrutura física de rede. A segmentação de rede, de forma geral, permite gerenciar e proteger melhor os recursos da rede, isolando dispositivos e definindo políticas de acesso entre eles.

