# TRIBOOT — Tahoe + SteamOS + Windows 11 + IA

Projeto guarda-chuva para o notebook Razer Blade Pro RZ09-0117 (2014), reunindo a arquitetura do futuro sistema tri-boot com:

- macOS Tahoe;
- SteamOS, quando a compatibilidade real com o hardware estiver validada;
- Windows 11;
- menu principal gráfico com IA para seleção, diagnóstico e recuperação.

## Arquitetura geral

Este repositório é o projeto principal de integração. Cada sistema deve permanecer desacoplado e ter seu próprio instalador, perfil e rotina de recuperação.

### 1. macOS Tahoe
Mantido no projeto específico:

- LOWDRUS INSTALLER;
- OpenCore;
- perfil Razer;
- diagnóstico, reparo e rollback;
- instalação e recuperação do Tahoe.

Repositório relacionado:
`lowdrus/AUTO-INSTALLER-TAHOE-NOTEBOOK-RAZER-BLADE-PRO-2014`

### 2. SteamOS
Objetivo futuro:
- validar suporte real ao hardware;
- definir estratégia de boot;
- preservar compatibilidade com o restante do tri-boot;
- automatizar instalação e recuperação.

Nenhuma versão deve ser considerada suportada antes de testes reais no Razer.

### 3. Windows 11
Objetivo futuro:
- instalação automatizada;
- drivers e pós-instalação;
- integração segura ao esquema de boot;
- recuperação sem afetar os outros sistemas.

### 4. Menu principal com IA
Camada superior do projeto, separada dos instaladores individuais.

Objetivos:
- interface gráfica de boot;
- seleção dos três sistemas;
- diagnóstico do estado de cada sistema;
- recuperação guiada;
- integração com os módulos LOWDRUS;
- suporte por voz/IA quando o ambiente técnico permitir;
- fallback seguro quando algum sistema não estiver disponível.

## Princípios do projeto

- nenhum instalador deve destruir outro sistema sem confirmação explícita;
- preservar mídia/EFI conhecida como funcional;
- manter backups e rollback;
- não assumir números fixos de disco;
- identificar discos por múltiplos atributos;
- separar UI, Engine, perfis de hardware e perfis de sistema operacional;
- automatizar o fluxo normal e deixar console técnico apenas como ferramenta avançada;
- atualizar componentes de forma versionada e auditável;
- não redistribuir payloads proprietários indevidamente.

## Estado atual

O trabalho ativo está concentrado primeiro no macOS Tahoe/LOWDRUS INSTALLER, porque ele precisa ficar estável antes da integração final do tri-boot.

Já existe:
- OpenCore funcional de contingência em mídia externa;
- perfil inicial do Razer;
- reconstrução/validação estrutural do Tahoe Builder;
- transporte TAR validado;
- LOWDRUS Engine e Desktop Manager em desenvolvimento;
- conceito de LOWDRUS Installer & Recovery;
- conceito de suporte remoto Desktop/ARATE ↔ Razer/ARATI.

Ainda pendente:
- instalação funcional completa do Tahoe;
- estabilização do LOWDRUS Installer;
- implementação real do SteamOS;
- implementação real do Windows 11;
- arquitetura final de partições;
- boot manager gráfico definitivo;
- camada de IA/voz;
- testes de atualização, rollback e recuperação dos três sistemas.

## Escopo

Este repositório não substitui os repositórios específicos de cada sistema. Ele documenta e integra o projeto completo de tri-boot.
