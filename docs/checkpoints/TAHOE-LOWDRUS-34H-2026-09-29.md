# TRIBOOT — integração Tahoe/LOWDRUS — checkpoint #34H

Data: 2026-09-29

O subprojeto Tahoe/LOWDRUS avançou da reconstrução canônica do InstallAssistant Apple até o transporte íntegro para a mídia LOWDRUS.

## Estado integrado
- `InstallAssistant.pkg` Apple: pacote versão `25.6.229`.
- Payload PBZX extraído e decodificado canonicamente.
- O `Info.plist` do `Install macOS Tahoe.app` extraído DIRETAMENTE do Payload Apple contém `25G227`; portanto 25G227 não deve ser tratado como erro do Builder nem reinvestigado sem nova evidência.
- Installer canônico reconstruído com o `SharedSupport.dmg` extraído do mesmo PKG Apple.
- SharedSupport canônico: `18,364,018,047` bytes; SHA-256 `72d8b6820595dc36ac27f43511c3b881dccb10b38ab60095085f3df9ce37d969`.
- 26 symlinks preservados.
- TAR canônico: `/LOWDRUS-TAHOE-CANONICAL.tar`.
- SHA-256 do TAR: `776466f38564a3e698a329930ce0a5c464c3363f4048d0022f106cf26a5f4c01`.
- Cópia validada no SSD Lexar 120 GB LOWDRUS em `G:\LOWDRUS-TRANSPORT\CANONICAL\LOWDRUS-TAHOE-CANONICAL.tar`.
- Tamanho no Windows: `18,419,875,840` bytes.
- SHA-256 no Lexar coincide exatamente com a origem.

## Nomenclatura obrigatória
- mídia física LOWDRUS = SSD Lexar 120 GB;
- `TOSHIBA External USB 3.0` = bridge/adaptador SATA→USB, NÃO o SSD;
- Samsung SATA ~512 GB = SSD interno do Razer;
- Netac = contingência OpenCore.

## Estado do bloqueio
O teste anterior do Builder V2 no Razer chegou a `startosinstall`, mas bloqueou em `com.apple.BuildInfo.preflight.error error 9`. O Builder V2 antigo NÃO é o artefato canônico atual. O novo artefato foi reconstruído diretamente dos componentes do PKG Apple e ainda precisa ser testado no Razer.

## Próximo passo global
Não iniciar Windows 11, SteamOS ou boot manager final. Prosseguir com Tahoe/LOWDRUS #34I: remoção segura da Lexar do Desktop → conectar ao Razer desligado → OpenCore/Recovery → extrair o TAR canônico nativamente → testar installer canônico. Só depois de Tahoe funcional ponta a ponta promover o estado do TRIBOOT.

Detalhes completos e itens NÃO REPETIR estão no checkpoint correspondente do repositório `lowdrus/AUTO-INSTALLER-TAHOE-NOTEBOOK-RAZER-BLADE-PRO-2014`.
