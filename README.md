# VulnChecker

> **Status do Projeto:** ⚠️ Work in Progress (Em desenvolvimento)

O **VulnChecker** é um script simples desenvolvido em Python projetado para automatizar a verificação de segurança da sua rede local. Ele captura automaticamente o seu endereço IP local do seu dispositivo e executa uma varredura simplificada via **Nmap** e compara os resultados diariamente para alertar sobre possíveis mudanças ou novas vulnerabilidades expostas.

---

##  Como Funciona?

1. **Coleta de IP e Varredura:** O script identifica o IP da sua interface de rede e roda o Nmap.
2. **Geração de Logs:** Os resultados do Nmap são salvos em um arquivo nomeado com a data do dia atual.
3. **Comparação Diária:** O script compara o arquivo de log de **hoje** com o de **ontem**.
4. **Tomada de Decisão:**
   * Se os arquivos forem iguais, nenhuma mudança foi detectada e o script encerra.
   * Se houver diferenças, ele exibe o conteúdo de ambos os dias na tela para análise (apenas se rodado manualmente pelo terminal, por cron job necessitaria de um outro arquivo que passa o output dos dois para a comparação direta) ⬆️ Possivel mudança futura para automatizar isso.
   * ⚠️ **Atenção:** Se o arquivo de ontem não existir, o script realiza a varredura de hoje e encerra para que o histórico comece a ser construído (ou voce pode só renomear o arquivo/criar um arquivo que contenha a data de ontem no formato YYYY-MM-DD, para fins de testes.)

---

## Como Executar

Para que o script cumpra seu papel de monitoramento contínuo, ele foi pensado para ser executado diariamente. Você pode fazer isso de duas formas:

* **Manualmente:** Executando o script uma vez por dia, que mostrará o output na tela do terminal, de uma forma mais dinamica.
* **Automaticamente:** Configurando uma tarefa no **Cron job** (Linux/macOS) para rodar o script em um horário fixo todos os dias.

---

## Dependencias

* Python 3.X.X
* Nmap 
* Sistema operacional que tenha base em unix/unix-like (para comandos como awk,ipconfig e etc.)
