# Montei meu próprio servidor DNS em casa — e descobri que muita gente usa uma rede pior sem perceber

Muita gente acredita que lentidão na internet sempre está relacionada apenas à velocidade contratada da sua operadora de internet. Mas depois que comecei a estudar mais sobre redes e infraestrutura, percebi que existe outro componente extremamente importante que quase ninguém olha: o **DNS**.

E foi uma das mudanças mais interessantes que fiz na minha rede doméstica.

Nos últimos meses, comecei a montar meu próprio **homelab** e a auto-hospedar alguns serviços aqui em casa usando o **CasaOS**. A ideia inicial era aprender mais sobre infraestrutura, cloud, redes, Linux e privacidade na prática. Mas esse projeto acabou crescendo.

> 📸 **<img width="1242" height="727" alt="1778620131842" src="https://github.com/user-attachments/assets/d361e0a7-c89b-45b1-9568-9e1870a825f3" />
**

Hoje, além do meu servidor DNS com **AdGuard Home**, o meu ecossistema doméstico conta com:
* 📂 Um servidor de arquivos centralizado;
* 🎬 **Jellyfin** para streaming de vídeo pessoal;
* 🎵 **Navidrome** como streaming de música;
* ☁️ **Nextcloud** como minha nuvem privada;
* 🎨 **Excalidraw** hospedado direto no meu servidor;
* 🔐 Acesso seguro aos meus arquivos fora de casa usando **VPN**;
* 🧪 Além de outros testes e serviços internos.

E foi justamente nesse processo de construir uma infraestrutura mais privada e independente que comecei a entender melhor como o DNS impacta praticamente toda a nossa experiência na internet.

---

## 🛑 O Impacto de um DNS Ruim

Mesmo em casas com conexões de internet rápida, um DNS problemático ou congestionado pode causar:
* Sites mais lentos para abrir;
* Aplicativos mais instáveis;
* Dispositivos demorando para responder;
* Páginas “travando” na primeira conexão;
* Menos privacidade dos seus dados de navegação.

Foi aí que resolvi estudar melhor o assunto e criar meu próprio servidor DNS local usando o **AdGuard Home**.

---

## 🗺️ Mas afinal, o que é DNS?

De forma simples, o DNS funciona como a **agenda telefônica da internet**. Quando digitamos um site como `youtube.com` ou `google.com`, nossos dispositivos precisam descobrir para qual endereço IP real aquela conexão deve ir. O DNS existe justamente para traduzir nomes amigáveis em endereços IP.

| O que digitamos | Para onde o DNS nos leva (IP Exemplo) |
| :--- | :--- |
| **google.com** | `142.250.xxx.xxx` |
| **youtube.com** | `142.250.xxx.xxx` |
| **instagram.com** | `157.240.xxx.xxx` |
| **netflix.com** | `52.xxx.xxx.xxx` |
| **github.com** | `140.82.xxx.xxx` |
| **linkedin.com** | `104.18.xxx.xxx` |

Na prática, toda navegação depende de consultas DNS acontecendo constantemente em segundo plano por todos os nossos dispositivos.

---

## ⚠️ O problema do DNS padrão da operadora

Na maioria das casas, o DNS utilizado é simplesmente o padrão configurado automaticamente pelo modem da operadora. O problema é que muitos provedores utilizam servidores com infraestruturas limitadas, mais lentos, menos estáveis e sem qualquer foco em privacidade ou bloqueio de domínios maliciosos.

> 📸 **<img width="1347" height="490" alt="1778622851183" src="https://github.com/user-attachments/assets/66160274-7fe4-489d-a5c4-de8b6b04ac1b" />
**

---

## 🛠️ Por que resolvi criar meu próprio DNS com AdGuard Home?

O projeto começou por pura curiosidade técnica e pelo desejo de não apenas consumir serviços prontos, mas entender o funcionamento real da minha rede doméstica.

O **AdGuard Home** atua como um servidor DNS local dentro da minha própria rede. Eu configurei o roteador principal da casa para apontar diretamente para o endereço IP do meu servidor onde o AdGuard Home está rodando.

> 📸 **<img width="1129" height="746" alt="1778621665760" src="https://github.com/user-attachments/assets/d5376312-7866-4315-93dd-360c93e33759" />
**

Agora, antes de qualquer dispositivo da casa acessar a internet, as consultas passam primeiro pelo meu servidor local.

### 🛡️ Benefícios práticos que obtive:
1. **Bloqueio de Trackers e Anúncios:** Filtra conexões em segundo plano geradas por aplicativos e Smart TVs para telemetria, publicidade e rastreamento.
2. **Segurança:** Impede o acesso a domínios conhecidos por espalhar malwares ou páginas de *phishing*.
3. **Cache DNS Local:** Como o servidor guarda as respostas localmente, as consultas repetidas são respondidas quase instantaneamente, sem precisar sair para a internet.

> 📸 **<img width="1089" height="595" alt="1778621768401" src="https://github.com/user-attachments/assets/998c662e-df05-41f2-8609-a30cb0d31880" />
**

A interface do AdGuard Home é extremamente amigável e me deu total autonomia, privacidade e controle da minha rede, diminuindo a dependência de serviços externos. Tudo isso rodando de forma leve no meu servidor.

> 📸 **<img width="1084" height="635" alt="1778621880914" src="https://github.com/user-attachments/assets/836f215c-1eac-469f-9ca0-0c0bec4828fe" />
**

> 📸 **<img width="1090" height="693" alt="1778622061910" src="https://github.com/user-attachments/assets/903963d1-e740-4817-bec4-124e80cc7352" />
**
---

## 💡 Alternativa simples: Melhores DNS Públicos

Nem todo mundo quer ou precisa montar um servidor em casa, mas qualquer pessoa pode mudar o DNS direto no painel do roteador para melhorar a experiência da rede doméstica. Aqui estão as melhores opções gratuitas e seguras do mercado:

* ⚡ **Cloudflare (`1.1.1.1` / `1.0.0.1`):** Conhecido pelo foco em máxima velocidade e baixa latência.
* 🛡️ **Quad9 (`9.9.9.9` / `149.112.112.112`):** Focado principalmente em segurança e bloqueio automático de domínios maliciosos.
* 🌐 **OpenDNS (`208.67.222.222` / `208.67.220.220`):** Uma das opções mais tradicionais do mercado, famosa pela estabilidade.
* ❌ **AdGuard DNS (`94.140.14.14` / `94.140.15.15`):** Excelente opção pública para quem busca bloqueio de anúncios e privacidade sem precisar instalar um servidor.
* 🦈 **Mullvad DNS (`194.242.2.2` / `194.242.2.3`):** Totalmente focado em privacidade estrita e redução de rastreamento.

---

## ⚙️ Como aplicar essa melhoria no seu roteador

Mudar o DNS é uma das melhorias mais simples e subestimadas que alguém pode fazer na rede doméstica. 

Se você quiser usar qualquer um dos DNSs citados acima e deixar sua rede mais segura, basta acessar o painel do seu roteador e alterar as configurações de LAN/DHCP. Você precisará adicionar o IP ao **DNS Primário** e, se desejar, um ao **DNS Secundário**.

* **Exemplo prático de combinação:**
  * **DNS Primário:** `94.140.14.14` (AdGuard)
  * **DNS Secundário:** `9.9.9.9` (Quad9)

Coloque os IPs correspondentes exatamente no local indicado no seu painel (como mostro no quadro vermelho da imagem abaixo) e não se esqueça de salvar as alterações depois!

> 📸 **<img width="1129" height="746" alt="1778625535122" src="https://github.com/user-attachments/assets/bcc17c52-c580-4a15-a453-3107b0215b8c" />
**

🔗 Para quem quiser pesquisar e utilizar outras opções, recomendo dar uma olhada nesta [Lista mais completa de provedores de DNS](https://adguard-dns.io/kb/pt-BR/general/dns-providers/).

---

## 🧠 O que esse projeto me ensinou

Esse laboratório prático foi muito além de apenas "instalar um serviço". Ele me forçou a entender conceitos fundamentais de:
* Redes e roteamento;
* Troubleshooting e análise de logs;
* Gerenciamento de containers no Linux;
* Segurança e privacidade de dados.

Isso prova que **infraestrutura de TI não precisa começar apenas dentro de grandes datacenters**. Um laptop antigo que estava encostado aqui em casa virou um laboratório fantástico que me ensina diariamente conceitos usados no ambiente profissional.

---

## 🔗 Referências e Materiais Úteis
* [Documentação Oficial do AdGuard Home](https://github.com/AdguardTeam/AdGuardHome)
* [O que é DNS? - Explicação da Cloudflare](https://www.cloudflare.com/learning/dns/what-is-dns/)
* [Projeto CasaOS](https://casaos.io/)
* [Meu artigo: Transformando um laptop antigo em servidor caseiro](https://www.linkedin.com/pulse/transformando-um-laptop-antigo-em-servidor-de-caseiro-alves--9us8f/)
