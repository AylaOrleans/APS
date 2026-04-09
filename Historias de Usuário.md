\# Histórias de Usuário — 08/04

\#\# HU-01 — Devolução com Avaria ou Extravio

\*\*Como\*\* atendente do balcão  
\*\*Quero\*\* registrar a devolução de um livro sinalizando danos físicos ou perda total  
\*\*Para\*\* aplicar a multa avaliada e bloquear o usuário até que o prejuízo seja ressarcido à faculdade

\#\#\# Cenários

\*\*Principal\*\*  
Dado que o livro voltou rasgado  
Quando o atendente digitar o valor da multa e confirmar  
Então o sistema deve gerar a pendência financeira e mudar o status do usuário para "Bloqueado"

\*\*Bloqueio de Erro\*\*  
Dado que o atendente marcou "Avaria"  
Quando tentar confirmar sem digitar um valor no campo de multa  
Então o sistema deve impedir a conclusão e exigir o preenchimento

\*\*Fluxo de Pagamento\*\*  
Dado que a multa foi gerada  
Quando o usuário optar por pagar na hora  
Então o sistema deve permitir selecionar “Dinheiro” e emitir o comprovante de quitação

\---

\#\# HU-02 — Renovação Online de Empréstimo

\*\*Como\*\* aluno da graduação  
\*\*Quero\*\* renovar meu livro através do sistema online  
\*\*Para\*\* estender meu prazo de entrega por mais 7 dias sem precisar ir à biblioteca física

\#\#\# Cenários

\*\*Principal\*\*  
Dado que o aluno não renovou o livro anteriormente e não há reservas  
Quando clicar em renovar  
Então o sistema deve atualizar a data de devolução para \+7 dias

\*\*Bloqueio por Limite\*\*  
Dado que o contador de renovação já está em "1/1"  
Quando o aluno tentar renovar novamente  
Então o sistema deve exibir: "Limite de renovação atingido. Apresente o livro no balcão"

\*\*Bloqueio por Reserva\*\*  
Dado que outro aluno reservou o livro  
Quando o usuário atual tentar renovar  
Então o sistema deve negar a ação informando que há uma fila de espera

\---

\#\# HU-03 — Bloqueio de Empréstimo de Obras de Referência

\*\*Como\*\* atendente do balcão  
\*\*Quero\*\* que o sistema identifique exemplares de "Referência" durante o empréstimo  
\*\*Para\*\* impedir que obras que não podem sair da biblioteca sejam emprestadas por engano

\#\#\# Cenários

\*\*Bloqueio de Empréstimo\*\*  
Dado que o livro bipado é da categoria "Referência"  
Quando o atendente tentar confirmar a saída  
Então o sistema deve emitir um alerta sonoro/visual e travar o botão de "Confirmar Empréstimo"

\*\*Bloqueio de Reserva\*\*  
Dado que um aluno pesquisa um livro de Referência  
Quando ele tentar reservar online  
Então o sistema deve informar que "Livros de Referência são apenas para consulta local"    
