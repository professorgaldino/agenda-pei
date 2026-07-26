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

## Distribuição automática por bimestre

Na opção **Bimestres**, o usuário cadastra as datas de início e término dos quatro períodos. Ao gerar uma agenda, o sistema:

1. identifica a qual bimestre pertence cada data;
2. procura no histórico a disciplina e o ano correspondentes àquele bimestre;
3. conta as aulas previstas na grade desde o início do período;
4. distribui as aulas em ordem cronológica, de segunda a sexta-feira.

Sábados e domingos não entram na contagem. Os períodos ficam salvos no documento do usuário no Firestore.

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
