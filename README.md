# Active Directory Hacking: Kerberoasting Attack 🏢

Este é o laboratório mais complexo do meu portfólio. Simulei uma infraestrutura corporativa completa (Windows Server 2022 + Active Directory) para executar ataques de identidade.

O objetivo foi explorar a técnica de **Kerberoasting**: solicitar um ticket de serviço (TGS) para uma conta vulnerável e extrair o hash da senha para quebra offline.

## ⚙️ Arquitetura do Lab
* **Domain Controller (DC):** Windows Server 2022 (Configurado com AD DS e DNS).
* **Atacante:** Kali Linux (Impacket Tools).
* **Rede:** Internal Network isolada com endereçamento estático.

## ⚔️ O Ataque (Passo a Passo)
1.  **Configuração do Alvo:** Criei um usuário de serviço (`lab_user1`) e registrei um SPN (Service Principal Name) para torná-lo vulnerável.
2.  **Bypass de Tempo:** Superei o mecanismo de segurança do Kerberos (Time Skew) sincronizando manualmente os relógios do DC e do Kali.
3.  **Extração:** Utilizei o script `GetUserSPNs.py` para solicitar o ticket TGS.

### 📸 Prova de Conceito (PoC)
A imagem abaixo mostra o sucesso do ataque: o DC validou a requisição e retornou o hash NTLMv2 do usuário alvo, que agora pode ser quebrado via Hashcat/John.

![Kerberoasting Hash](kerberoasting_proof.png)

## 🧠 Aprendizado
Este lab consolidou meu conhecimento em:
* Administração de Windows Server e Active Directory.
* Protocolo Kerberos e suas falhas de design.
* Troubleshooting avançado de redes (DNS, Firewall e NTP).

---
*Projeto realizado em ambiente virtual isolado.*
