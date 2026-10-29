# Como cheguei à conclusão

## A pergunta

Queria entender onde estaria uma oportunidade para estimular uma nova compra entre os clientes da Olist. Antes de pensar em uma ação, precisei decidir o que contaria como recompra e verificar se os grupos de clientes poderiam ser comparados de forma justa.

## Primeiro, entendi as tabelas

Explorei nulos, vazios, tipos de dados e duplicatas. Depois conferi o que cada linha representa. Um pedido pode ter vários itens e pagamentos, então contar linhas dessas tabelas como compras aumentaria o número de pedidos. Usei `order_id` para identificar pedidos e `customer_unique_id` para acompanhar a mesma pessoa.

Considerei apenas pedidos entregues. Para dar a todos o mesmo prazo de observação, acompanhei clientes cuja primeira compra entregue foi feita de janeiro de 2017 a maio de 2018 e procurei novas compras até agosto de 2018.

## A definição de recompra mudou a leitura

Comecei pelo segundo pedido entregue em até 90 dias. Encontrei **1.711 clientes**, ou **2,28%** dos 75.123 analisados. Ao medir o intervalo entre os pedidos, vi que **781 segundos pedidos** aconteceram nas primeiras 24 horas. Isso enfraqueceu minha ideia inicial de que todo segundo pedido representava uma nova ocasião de compra.

Por isso, também medi qualquer nova compra entregue feita **mais de 24 horas** depois da primeira, dentro dos mesmos 90 dias. Foram **958 clientes**, ou **1,28%**. Procurei qualquer pedido posterior a 24 horas, mesmo quando o segundo pedido ocorreu antes desse prazo. Mantive as duas taxas no notebook para deixar clara a diferença entre as regras.

## O que testei depois

Quis saber quando os clientes voltavam e se a taxa mudava ao longo do tempo. A faixa com mais retornos depois de 24 horas foi a de **7 a 30 dias**, com **340 clientes**, mas nenhuma faixa concentrou a maioria sozinha. A comparação entre janeiro e maio de 2017 e o mesmo período de 2018 não mostrou uma queda clara na taxa após 24 horas.

Também comparei o peso do frete e o valor dos produtos no primeiro pedido. Nesse corte, as taxas após 24 horas ficaram parecidas entre as faixas. Essas hipóteses não trouxeram um sinal claro para priorizar uma ação.

O tipo do primeiro pedido foi mais interessante. Clientes que começaram com produtos diferentes tiveram uma taxa maior de nova compra após 24 horas, inclusive quando comparei períodos e faixas de valor. Ainda assim, esse grupo é pequeno: **2.417 clientes**, com **50 novas compras**. A relação observada não prova que comprar produtos diferentes faz alguém voltar.

## Onde eu começaria

Os **67.627 clientes** que compraram **um item** no primeiro pedido representam cerca de **90% da base**. A taxa de nova compra após 24 horas nesse grupo foi de **1,22%**. Pelo tamanho do grupo e pela taxa observada, eu começaria por ele para testar uma recomendação de produtos complementares depois da primeira entrega.

Os dados mostram quem voltou e quando isso aconteceu. Eles não mostram o efeito de campanhas, nem permitem afirmar que a recomendação aumentaria a recompra. Para saber isso, seria preciso comparar clientes escolhidos de forma aleatória para receber ou não a ação, usando o mesmo prazo de acompanhamento.

O [notebook](Notebooks/Analise_de_Recompra_Olist.ipynb) registra os testes e os resultados de cada etapa.
