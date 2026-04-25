📊 Análise 1 — Receita por Cliente (Pareto)
🎯 Pergunta de negócio
Quais clientes geram mais receita e qual o nível de concentração da base?

🧠 Query
sql-- Top 15 clientes por receita total
-- Base: 136 clientes com ao menos 1 compra registrada
SELECT 
    c.idcliente,
    c.cliente, 
    SUM(v.total) AS receita_total
FROM vendas v 
INNER JOIN clientes c 
    ON v.idcliente = c.idcliente 
GROUP BY c.idcliente, c.cliente 
ORDER BY receita_total DESC 
LIMIT 15;

📁 Dados

CSV: resultados/receita_por_cliente.csv


📊 Visualização

Gráfico de barras com os 15 principais clientes por receita
Arquivo: resultados/receita_por_cliente.png


⚠️ Qualidade dos Dados

Base contém 1.000 clientes únicos cadastrados
864 clientes sem nenhuma venda registrada (~86% da base)
Possível oportunidade de investigação sobre a origem desses cadastros inativos


🔍 Insights

46% da receita total está concentrada em apenas 15 clientes
Apenas 136 de 1.000 clientes realizaram compras (~13,6% da base)


🧠 Interpretação
Os dados indicam uma forte concentração de receita em poucos clientes, evidenciando dependência da empresa em uma pequena parcela da base.
Além disso, observa-se baixa ativação de clientes, com a grande maioria nunca tendo gerado receita.

💡 Recomendações

Criar programas de fidelização para clientes de alto valor (ex: categorias Ouro, Prata, Bronze)
Implementar campanhas de reativação para clientes inativos
Desenvolver estratégias de incentivo à primeira compra
Trabalhar segmentação da base para aumentar conversão


📌 Conclusão
A análise evidencia um cenário clássico de concentração de receita (efeito Pareto), combinado com baixa ativação da base.
Isso sugere oportunidades claras tanto em retenção de clientes estratégicos quanto na expansão da base ativa.
