-> 1. Por que a Secret aparece no log como *** e a variável aparece normalmente?

O GitHub utiliza um mecanismo de "masking" para segredos. Ele monitora a saída do console e oculta qualquer valor que corresponda a um Secret cadastrado para evitar vazamento de credenciais. Já as Variables são tratadas como configurações comuns e ficam visíveis para facilitar o monitoramento.



-> 2. O Job deploy_app consegue ler a variável BUILD_VERSION criada no Job build_app? Por quê?

Não. Cada Job roda em uma máquina virtual isolada. Variáveis de ambiente definidas no escopo de um Job são exclusivas dele. Para compartilhar dados entre Jobs, seria necessário usar outputs ou artifacts.