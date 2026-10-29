# Onde está a oportunidade de recompra na Olist?

Neste projeto, investiguei a recompra dos clientes da Olist para responder a uma pergunta de marketing: **qual grupo eu priorizaria para testar uma ação que incentive uma nova compra?**

O foco do trabalho é mostrar meu raciocínio. No [notebook](Notebooks/Analise_de_Recompra_Olist.ipynb), começo explorando as tabelas, levanto hipóteses, testo cada uma e explico como cheguei à conclusão.

Para uma leitura mais rápida, reuni as decisões principais em [Como cheguei à conclusão](Como_cheguei_a_conclusao.md).

## O que encontrei

- Analisei **75.123 clientes** cuja primeira compra entregue foi feita entre janeiro de 2017 e maio de 2018. Observei novas compras até agosto de 2018.
- **2,28%** fizeram um segundo pedido entregue em até 90 dias. Porém, muitos segundos pedidos ocorreram quase ao mesmo tempo que o primeiro.
- Ao considerar qualquer nova compra entregue feita **mais de 24 horas** depois da primeira, a taxa foi de **1,28%**.
- Clientes que compraram **um item** no primeiro pedido representam cerca de **90% da base** e tiveram taxa de nova compra após 24 horas de **1,22%**. Pelo tamanho desse grupo, eu começaria por ele para testar uma ação de retorno.

Essa é uma **oportunidade para teste**, não uma previsão de resultado. Os dados não mostram campanhas realizadas nem provam que recomendar produtos fará os clientes voltarem.

## Como reproduzir a análise

1. Baixe os nove arquivos CSV do [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).
2. Crie a pasta `OlistDados` na raiz deste projeto e coloque os CSVs diretamente nela, sem outra subpasta.
3. Na raiz do projeto, instale as bibliotecas com `python -m pip install -r requirements.txt`.
4. Abra a **pasta do projeto** no VS Code e execute o [notebook](Notebooks/Analise_de_Recompra_Olist.ipynb) do início ao fim. Também é possível iniciar o Jupyter pela raiz com `python -m jupyter lab`.

O notebook usa `Path("OlistDados")`, então a pasta de trabalho da execução precisa ser a raiz do projeto. Os CSVs não fazem parte deste repositório; o link acima é a fonte dos dados.

## Como defini recompra

Identifiquei a pessoa pelo `customer_unique_id` e cada compra pelo `order_id`. Considerei apenas pedidos com status `delivered`. O intervalo é calculado entre os horários de `order_purchase_timestamp`.

Mostro duas taxas porque a definição muda bastante o resultado:

- **Segundo pedido em até 90 dias:** o próximo pedido distinto da pessoa após o primeiro.
- **Nova compra após 24 horas:** qualquer pedido distinto feito mais de 24 horas depois do primeiro e dentro de 90 dias, mesmo que o segundo pedido tenha ocorrido antes das 24 horas.

O corte de maio de 2018 dá aos clientes pelo menos 90 dias de observação até o fim de agosto de 2018. As escolhas de 24 horas e 90 dias são regras da análise e são discutidas no notebook.

## Ferramentas

Python, pandas, Matplotlib e Jupyter Notebook.
