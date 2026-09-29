# TRIBOOT — HANDOFF / ESTADO ATUAL

> **Fonte de continuidade entre chats para o projeto guarda-chuva TRIBOOT.** Este arquivo existe para que a evolução do tri-boot não dependa da memória de uma conversa específica.
>
> Última atualização: 2026-09-29.

## 1. Regra de retomada em qualquer novo chat

Antes de propor mudanças no projeto TRIBOOT, ler nesta ordem:

1. `docs/HANDOFF-CURRENT-STATE.md`;
2. `README.md`;
3. `docs/ARCHITECTURE.md`;
4. `docs/ROADMAP.md`;
5. o handoff do subprojeto ativo, quando aplicável.

Para o macOS Tahoe/LOWDRUS, consultar também:

`lowdrus/AUTO-INSTALLER-TAHOE-NOTEBOOK-RAZER-BLADE-PRO-2014/docs/HANDOFF-CURRENT-STATE.md`

**Não repetir testes já concluídos em subprojetos sem mudança real de hardware, artefato ou hipótese.**

## 2. Papel deste repositório

Este é o **projeto guarda-chuva** do Razer Blade Pro RZ09-0117 (2014). Ele não deve duplicar integralmente os repositórios específicos. Sua função é manter a visão sistêmica e a integração de:

- macOS Tahoe;
- SteamOS;
- Windows 11;
- camada de boot/seleção;
- GUI principal;
- IA/voz;
- diagnóstico;
- recuperação;
- rollback;
- atualizações;
- política de partições;
- proteção entre sistemas;
- integração dos instaladores individuais.

## 3. Arquitetura-alvo do TRIBOOT

Cada sistema permanece desacoplado e possui seu próprio instalador/profile/recovery, enquanto o TRIBOOT atua como orquestrador superior.

### macOS Tahoe

Responsabilidade principal no repositório LOWDRUS INSTALLER:

`lowdrus/AUTO-INSTALLER-TAHOE-NOTEBOOK-RAZER-BLADE-PRO-2014`

Estado atual do Tahoe deve ser lido do HANDOFF desse repositório. Em 2026-09-29, o trabalho ativo está concentrado na reconstrução canônica do `Install macOS Tahoe.app` a partir do `InstallAssistant.pkg` Apple original, com checkpoint #34B concluído e próximo #34C.

### Windows 11

Objetivos preservados:

- instalação automatizada;
- drivers e pós-instalação;
- integração segura ao esquema de boot;
- recuperação sem destruir macOS/SteamOS;
- futura experiência GUI/one-click;
- suporte a reinstalação limpa e preservação de dados com confirmação explícita.

### SteamOS

Objetivos preservados:

- validar suporte real ao hardware do Razer;
- selecionar distribuição/estratégia compatível somente após teste real;
- preservar coexistência com Tahoe e Windows 11;
- automatizar instalação, boot e recuperação;
- não promover suporte antes de validação real.

### Menu principal gráfico + IA

Camada superior do projeto.

Objetivos:

- selecionar Tahoe / SteamOS / Windows 11;
- diagnosticar o estado de cada sistema;
- reparar/recovery guiado;
- mostrar saúde de discos, boot entries e partições;
- incorporar assistência por IA/voz quando o ambiente permitir;
- possuir fallback seguro sem IA/rede;
- nunca exigir Terminal/PowerShell no fluxo normal do usuário;
- console técnico somente em Ferramentas Avançadas.

## 4. Regras de segurança globais

1. Nunca apagar outro sistema implicitamente.
2. Identificar discos por múltiplos atributos; nunca apenas `diskN` ou letra.
3. Exibir claramente disco físico, volume, tamanho e sistema antes de qualquer ação destrutiva.
4. Toda instalação limpa exige confirmação explícita.
5. Preservar EFI/recovery/mídia conhecida como funcional.
6. Manter backup e rollback antes de mudanças críticas.
7. Um sistema não pode reconfigurar silenciosamente o boot de outro.
8. Qualquer falha parcial deve bloquear promoção para `[OK]`.
9. Logs e checkpoints precisam sobreviver a reboot e mudança de chat.
10. O produto final deve ser GUI/one-click; comandos manuais pertencem ao desenvolvimento/contingência.

## 5. Relação entre TRIBOOT e LOWDRUS

O LOWDRUS INSTALLER é o subprojeto responsável pelo Tahoe. O TRIBOOT não deve copiar todos os logs técnicos do LOWDRUS; deve registrar:

- qual versão/estado do LOWDRUS está integrada;
- se a instalação Tahoe já é funcional ponta a ponta;
- contrato de integração com boot manager;
- partições/volumes que precisam ser preservados;
- entradas de boot esperadas;
- recovery e rollback disponíveis;
- dependências de hardware relevantes.

Quando o LOWDRUS alcançar instalação Tahoe funcional ponta a ponta, o TRIBOOT deve atualizar seu estado e liberar a próxima fase de integração.

## 6. Estado global atual

### Tahoe / LOWDRUS

**ATIVO / prioridade atual.** Ainda não considerado funcional ponta a ponta.

Último estado conhecido deve ser lido do HANDOFF do LOWDRUS. Em 2026-09-29:

- Builder V2 anterior chegou ao Razer e `startosinstall` foi executado;
- bloqueio observado: `com.apple.BuildInfo.preflight.error error 9`;
- investigação levou à decisão de reconstruir canonicamente a partir do PKG Apple original;
- distro dedicada `LOWDRUS-BUILDER` em F: está operacional;
- ferramentas `xz`, `cpio`, `python3`, `git`, `build-essential` já instaladas;
- checkpoint #34B concluído;
- próximo passo: #34C.

### Windows 11

**PENDENTE de implementação real no TRIBOOT.** Não considerar instalado/automatizado apenas por existirem ISOs locais.

### SteamOS

**PENDENTE de validação real.** Não assumir compatibilidade antes de teste no Razer.

### Boot manager gráfico / IA

**CONCEITO definido, implementação final pendente.** Deve depender de contratos estáveis dos três instaladores, não o contrário.

## 7. Itens que o TRIBOOT final deverá fazer

- inventariar hardware e discos;
- detectar instalações existentes;
- mostrar mapa visual de partições;
- oferecer instalação/reinstalação/repair de cada OS;
- permitir instalação limpa com confirmação explícita;
- preservar automaticamente volumes protegidos;
- preparar/atualizar boot entries;
- validar integridade antes/depois;
- manter recovery próprio;
- manter histórico de operações;
- sincronizar estado dos subprojetos;
- suportar update versionado pelo GitHub;
- oferecer rollback de atualização;
- fornecer modo offline sempre que possível;
- integrar IA/voz apenas como camada assistiva, nunca como dependência crítica.

## 8. Nomenclatura crítica de mídia

Para evitar confusão herdada do desenvolvimento LOWDRUS:

- mídia física LOWDRUS Installer = **SSD Lexar 120 GB**;
- `TOSHIBA External USB 3.0` = identificação do **bridge/adaptador SATA→USB**, não o SSD;
- SSD interno do Razer = Samsung SATA ~512 GB;
- Netac = mídia OpenCore de contingência;
- Kingston `LWIFI_TEST` = pendrive experimental.

O TRIBOOT deve sempre separar **mídia física** de **bridge/adaptador reportado pelo sistema operacional**.

## 9. Política de documentação daqui em diante

Após cada marco global, atualizar este HANDOFF com:

- estado de cada OS;
- dependências entre subprojetos;
- decisões de arquitetura;
- esquema de partições/boot validado;
- checkpoints concluídos;
- itens NÃO REPETIR;
- próximo passo global.

Detalhes técnicos profundos permanecem nos repositórios específicos e são referenciados daqui.

## 10. Próximo passo global

**Não iniciar Windows 11, SteamOS ou o boot manager final agora.**

Primeiro concluir o fluxo Tahoe/LOWDRUS até instalação funcional ponta a ponta. O próximo passo técnico imediato continua sendo o **#34C no repositório LOWDRUS**. Depois que Tahoe estiver estável, atualizar este HANDOFF e avançar para a definição final do layout de partições/boot do TRIBOOT.