# Arquitetura do TRIBOOT

```
                 TRIBOOT / IA
                      |
          +-----------+-----------+
          |           |           |
        Tahoe      SteamOS     Windows 11
          |           |           |
      LOWDRUS      Installer    Installer
      Installer     futuro       futuro
          |
   OpenCore / Perfil Razer
```

## Regra de integração

Cada sistema operacional é responsável por sua própria instalação e recuperação. A camada TRIBOOT coordena seleção, estado e transições entre sistemas, mas não deve duplicar a lógica interna dos instaladores.

## Futuro menu IA

O menu principal deverá ser uma camada de boot/orquestração com:
- interface gráfica;
- estado dos sistemas;
- seleção de sistema;
- diagnóstico;
- recuperação;
- integração com logs;
- voz/IA quando tecnicamente viável.

A IA não deve ser um ponto único de falha: sempre haverá um caminho de boot convencional/fallback.

## Segurança

- Netac/EFI conhecida como funcional é contingência durante o desenvolvimento;
- operações destrutivas devem exigir identificação forte do alvo;
- cada alteração de boot deve possuir rollback;
- o projeto deve evitar sobrescrever EFI conhecida como boa sem backup;
- instalações devem preservar os outros sistemas sempre que o layout suportar isso.
