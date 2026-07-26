# AgendaFácil — publicação web

Esta pasta contém somente os arquivos fundamentais para publicar e manter a aplicação.

## Arquivos

- `index.html`: aplicação web completa em arquivo único, com interface, estilos, React e Firebase.
- `firestore.rules`: segurança do banco; cada usuário autenticado acessa somente os próprios dados.
- `firebase.json`: configuração das regras do Firestore.
- `.firebaserc`: identifica o projeto Firebase `agenda-pei-fd137`.

## Arquitetura

- Hospedagem: GitHub Pages.
- Autenticação: e-mail e senha pelo Firebase Authentication.
- Banco de dados: Cloud Firestore.
- Dados de cada usuário: `users/{uid}/agenda/state`.
- Dados armazenados: professor, grade, disciplinas, aulas, habilidades, bimestres, revisões e configurações da agenda.

## Publicação no GitHub Pages

Coloque todos os arquivos desta pasta diretamente na raiz do repositório. Em **Settings → Pages**, escolha:

- Source: `Deploy from a branch`
- Branch: `main`
- Folder: `/ (root)`

## Configuração obrigatória do Firebase

No projeto `agenda-pei-fd137`:

1. Abra **Authentication → Sign-in method**.
2. Ative o provedor **E-mail/senha**.
3. Crie o **Firestore Database**, caso ainda não exista.
4. Publique o conteúdo de `firestore.rules` em **Firestore → Rules**.
5. Adicione o domínio do GitHub Pages em **Authentication → Settings → Authorized domains**.

O provedor Google pode ser desativado, pois a aplicação não o utiliza mais.

## Código-fonte para futuras alterações

O código-fonte editável está em:

`C:\Users\sique\OneDrive\Documentos\bqsytems\automacao-agenda-pei-backup-2026-07-26`

Depois de uma alteração, execute nessa pasta:

```powershell
npm.cmd run build:github
```

O arquivo gerado em `publicar-no-github\index.html` deve substituir o `index.html` desta pasta.
