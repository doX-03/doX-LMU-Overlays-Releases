# doX LMU Overlays Releases

Repositório público de distribuição do doX LMU Overlays. Ele não contém o
código-fonte do plugin nem do updater.

O plugin consulta o `manifest.json` publicado na branch `main`. Quando houver
uma versão nova, o manifesto aponta para um asset imutável de uma GitHub
Release. Esse asset é um pacote ZIP com a DLL, os overlays e o updater.

## Estrutura de um pacote de atualização

```text
doX-update-<versão>.zip
├── doX-Updater.exe
├── doX.LMU_SessionDataPlugin.dll
├── overlays/
├── doX-LMU-Overlays.version
└── manifest.json
```

O `doX-Updater.exe` é extraído apenas para uma pasta temporária pelo plugin;
ele não é instalado de forma permanente no SimHub nem é iniciado com o Windows.

## Publicar uma versão

1. Monte o ZIP e calcule o SHA-256 dele.
2. Crie uma GitHub Release com a tag `v<versão>` e envie o ZIP como asset.
3. Atualize o `manifest.json` na branch `main` com a versão, URL do asset e
   SHA-256.
4. Só depois publique o commit do manifesto.

O manifesto ativo deve sempre apontar para um asset já publicado. Use
`manifest.example.json` como modelo.

O OverTake continua sendo o canal oficial para apresentação, notas e download
manual do pack.
