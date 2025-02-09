# roboDeAlteracaoDeHorarioDeAtendimentoTecnico

Case de Robô de Alteração de Horários

Esse projeto foi de extrema importância, pois atuava na redução de custos diretamente.
Alcançou grande expressividade e é utilizado até hoje.

Cada ponto de caixa eletrônico trabalha com horário equivalente ao do estabelecimento em que está alocado.
Existe o horário de atendimento do cliente, que é o que é passado para o público, e o horário de atendimento técnico, que é o horário em que podemos fazer nossas manutenções.

Alguns estabelecimentos, como shoppings, não permitem que as manutenções sejam feitas no horário em que o shopping está aberto. Exemplo: o shopping abre às 10h, então a manutenção precisa ser realizada das 8h às 10h ou de madrugada.
Alguns estabelecimentos trabalham aos feriados e outros não; alguns abrem aos sábados, outros meio período; alguns aos domingos, outros não.

Sendo assim, caso tivéssemos algum incidente no Caixa Eletrônico 24 HORAS, nosso sistema identificaria, de acordo com o horário de atendimento técnico, se o estabelecimento que contém o caixa pode receber a tratativa. Caso contrário, o chamado que tinha sido associado ao operador automaticamente é retirado da sua fila de atendimento, evitando visita improdutiva e gastos com deslocamento e hora técnica (mão de obra).

Entendendo essa regra de negócio, resolvemos atualizar o horário de atendimento técnico para todos os aproximadamente 24 mil caixas.

Nos deparamos com um número inicial próximo de 48.000 registros de alterações de horário. Sempre era o dobro, pois temos horários de atendimento intra-cofre e extra-cofre para cada ponto.

No início, resolvemos separar alguns recursos da equipe (3 ou 4 pessoas) para alterar os horários.
Cada alteração, feita manualmente, levava aproximadamente 3 minutos.
Uma pessoa, em uma hora, fazia 20 alterações, multiplicadas por 8 horas trabalhadas, resultava em 160 alterações por dia.
Fazíamos essas atualizações semanalmente.

Cálculo do tempo e custo manualmente
Para cobrir essa atividade com recursos humanos:
48.000 alterações / 160 alterações por funcionário / 7 dias = 43 pessoas por semana fazendo somente isso.
Custo: Apenas considerando salários, aproximadamente R$ 4.000 por funcionário × 43 = R$ 172.000 de mão de obra.

Cálculo do tempo e custo com o robô
O robô realizava a atividade 24h sem parar e levava cerca de 1 minuto para cada alteração.
24 × 60 = 1.440 alterações/dia.
1.400 alterações que uma pessoa levaria cerca de 9 dias para fazer, o robô fazia em um único dia.
Custo: Com o robô, uma máquina de R$ 5.000 já era suficiente.

Esse é o impacto de uma atividade robotizada.

Demoramos cerca de um mês para ajustarmos todos os horários.

Após isso, apenas as manutenções semanais variavam entre 2.000 a 5.000 alterações.
Mesmo assim, se tivéssemos que alterar manualmente, precisaríamos de 2 a 4 recursos humanos, representando uma economia de R$ 4.000 a R$ 12.000 por mês.
Além disso, otimizamos os custos, evitando visitas improdutivas.

Execução:

Temos uma ferramenta de banco de dados que nos mostra a quantidade de transações no caixa por hora.
Filtramos essas transações por horários e analisamos os períodos em que o caixa é utilizado.

Exemplo:
Se o estabelecimento onde o caixa está localizado abre às 8h, começamos a notar transações a partir desse horário e verificamos que as transações encerram às 22h.
Nesse caso, o horário de atendimento técnico era configurado das 8h às 22h durante a semana.
Aos sábados, o transacional era das 8h às 14h e, aos domingos, não havia transações, então sabíamos os horários adequados de cada ponto de atendimento.

Extraíamos os dados para o Excel, aplicávamos diversas fórmulas e filtros para identificar os horários corretos ou errados e, então, fazíamos as alterações necessárias.

Após essa análise primária e extração dos dados, o Python entrava em ação.

Todos os horários eram alterados com PyAutoGUI, utilizando cliques, tabs, copy-paste e typewrite para inserir os dados corretamente.

Esse era o funcionamento do processo.

Não postei o código enquando estava trabalhando na empresa mas esse o funcionamento do processo e foi desenvolvido por mim.

=====================================

Vantagens da utilização de robos:

    * Não comete erros de digitação.
    * Não comete erros de click em lugares errados.
    * Não comete erros operacionais.
    * Não insere dados errados. 
    * Não deleta dados equivocadamete. 
    * Economiza tempo de mão de obra. 


Utilizamos os comandos do Pyautogui e Time para realização desse projeto.


Aqui estão os comandos do PyAutoGUI para as funções que você mencionou:
1. Click (Clique Simples)

pyautogui.click(x=100, y=200)  # Clica na posição (100, 200)

Se quiser clicar onde o mouse está atualmente:

pyautogui.click()

2. DoubleClick (Clique Duplo)

pyautogui.doubleClick(x=100, y=200)  # Clique duplo na posição (100, 200)

Ou onde o mouse está:

pyautogui.doubleClick()

3. time.sleep (Pausa)

time.sleep(2)  # Pausa por 2 segundos

4. typewrite (Digitar Texto)

pyautogui.typewrite("Olá, mundo!", interval=0.1)  # Digita com 0.1s de intervalo entre caracteres

5. hotkey (Atalhos de Teclado), para clicar em duas teclas juntas:

pyautogui.hotkey('ctrl', 'c')  # Pressiona Ctrl+C (Copiar)
pyautogui.hotkey('ctrl', 'v')  # Pressiona Ctrl+V (Colar)
pyautogui.hotkey('alt', 'tab')  # Alterna entre janelas

6. Pegar a Posição do Clique

Para descobrir onde está o cursor do mouse:

x, y = pyautogui.position()
print(f"Posição do mouse: {x}, {y}")

Ou para exibir em tempo real:

while True:
    print(pyautogui.position())
    time.sleep(1)  # Atualiza a posição a cada 1 segundo

