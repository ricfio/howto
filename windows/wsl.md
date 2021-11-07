# WSL

## Move all WSL Distributions on other drive

Use 'Windows PowerShell' as shell for the following commands.

1. List WSL distributions state with `wsl --list --all --verbose`

    ```console
      NAME                   STATE           VERSION
    * Ubuntu                 Running         2
      docker-desktop         Stopped         2
      docker-desktop-data    Stopped         2
    ```

2. Terminate all WSL running distributions with `wsl --terminate <Distribution>`

    ```powershell
    wsl --terminate Ubuntu
    wsl --list --all --verbose
    ```

    ```console
      NAME                   STATE           VERSION
    * Ubuntu                 Stopped         2
      docker-desktop         Stopped         2
      docker-desktop-data    Stopped         2
    ```

3. Export all WSL distributions on tar files with `wsl --export <Distribution> <ExportFile>`

    ```powershell
    mkdir E:\TEMP\wsl
    cd E:\_TEMP\wsl
    wsl --export Ubuntu Ubuntu.tar
    wsl --export docker-desktop docker-desktop.tar
    wsl --export docker-desktop-data docker-desktop-data.tar
    ```

4. Unregister all WSL distributions with `wsl --unregister <Distribution>`

    ```powershell
    wsl --unregister Ubuntu
    wsl --unregister docker-desktop
    wsl --unregister docker-desktop-data
    wsl --list --all --verbose
    ```

    ```console
      NAME                   STATE           VERSION
    ```

5. Import all WSL distributions with `wsl --import <Distribution> <InstallPath> <ExportFile> [Options]`

    ```powershell
    mkdir D:\wsl
    cd E:\_TEMP\wsl
    mkdir D:\wsl\Ubuntu
    wsl --import Ubuntu D:\wsl\Ubuntu Ubuntu.tar --version 2
    mkdir D:\wsl\docker-desktop
    wsl --import docker-desktop D:\wsl\docker-desktop docker-desktop.tar --version 2
    mkdir D:\wsl\docker-desktop-data
    wsl --import docker-desktop-data D:\wsl\docker-desktop-data docker-desktop-data.tar --version 2
    wsl --list --all --verbose
    ```

    ```console
      NAME                   STATE           VERSION
    * Ubuntu                 Stopped         2
      docker-desktop         Stopped         2
      docker-desktop-data    Stopped         2
    ```

6. Ubuntu will use root as the default user, go to the Ubuntu App Folder to switch back to previous default user

    ```powershell
    ubuntu config --default-user <username>
    ```

## References

- [https://superuser.com/questions/1550622/move-wsl2-file-system-to-another-drive]
- [https://avinal.space/posts/development/wsl1.html]
- [https://serverfault.com/questions/975980/how-to-move-docker-images-to-other-drive-in-windows]

## Appendix

### WSL Help

`wsl --help`

```console
Copyright (c) Microsoft Corporation. Tutti i diritti sono riservati.

Sintassi: wsl.exe [Argument] [Options...] [CommandLine]

Argomenti per l’esecuzione di file binari di Linux:

    Se non viene specificata alcuna riga di comando, wsl.exe avvia la shell predefinita.

    --exec, -e <CommandLine>
        Esegue il comando specificato senza usare la shell di Linux predefinita.

    --
        Passa la riga di comando rimanente così com’è.

Opzioni:
    --distribution, -d <Distro>
        Esegue la distribuzione specificata.

    --user, -u <UserName>
        Esegue come l’utente specificato.

Argomenti per la gestione del sottosistema Windows per Linux:

    --help
        Visualizza informazioni sull’utilizzo.

    --install [Opzioni]
        Installa ulteriori distribuzioni del sottosistema di Windows per Linux.
        Per una lista di distribuzioni valide, usa 'wsl --list --online'.

        Opzioni:
            --distribution, -d [Argomento]
                Scarica e installa una distribuzione per nome.

                Argomenti:
                    Un valido identificatore di distribuzione (senza distinzione tra maiuscole e minuscole).

                Esempi:
                    wsl --install -d Ubuntu
                    wsl --install --distribution Debian

    --set-default-version <Versione>
        Modifica la versione di installazione predefinita per le nuove distribuzioni.

    --shutdown
       Termina immediatamente tutte le distribuzioni in esecuzione e della macchina virtuale leggera
        WSL 2.

    --status
        Mostra lo stato del sottosistema Windows per Linux.

    --update [Opzioni]
        Se non vengono specificate opzioni, il kernel WSL 2 verrà aggiornato
        all'ultima versione.

        Opzioni:
            --rollback
                Ripristina la versione precedente del kernel WSL 2.

Argomenti per la gestione delle distribuzioni nel sottosistema Windows per Linux:

    --export <Distro> <Nomefile>
        Esporta la distribuzione in un file tar.
        Il nome del file può essere - per l'output standard.

    --import <Distro> <PercorsoInstallazione> <Nomefile> [Opzioni]
        Importa il file tar specificato come una nuova distribuzione.
        Il nome del file può essere - per l'input standard.

        Opzioni:
            --version <Versione>
                Specifica la versione da utilizzare per la nuova distribuzione.

    --list, -l [Options]
        Elenchi di distribuzioni.

        Opzioni:
            --all
                Elenco di tutte le distribuzioni, incluse quelle
                attualmente installate o disinstallate.

            --running
                Solo gli elenchi di distribuzioni che sono in esecuzione.

            --quiet, -q
                Mostra solo i nomi delle distribuzioni.

            --verbose, -v
                Mostra informazioni dettagliate su tutte le distribuzioni.

            --online,-o
                Visualizza un elenco di distribuzioni disponibili per l'installazione con 'wsl--install'.

    --set-default,-s <Distro>
        Imposta la distribuzione come predefinita.

    --set-version <Distro><Version>
        Modifica la versione della distribuzione specificata.

    --terminate, -t <Distro>
         Termina la distribuzione specificata.

    --unregister <Distro>
       Annulla la registrazione della distribuzione ed elimina il file system radice.
```
