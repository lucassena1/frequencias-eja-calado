# Frequência EJA

Aplicação web inicial para importar e conferir relatórios mensais de frequência da EJA.

## Executar

Abra `index.html` em um navegador com internet. A leitura de PDFs usa PDF.js carregado do CDN. Para servir localmente, por exemplo:

```bash
python3 -m http.server 8000 --directory .
```

Depois acesse `http://localhost:8000`.

## Implantação estática na Vercel

O `index.html` pode ser implantado como site estático. Configure o diretório raiz como `frequencia-eja` e deixe o build command vazio; o arquivo de entrada é `index.html`.

## Estado atual e próximos passos

- Esta versão guarda dados no `localStorage` do navegador e processa PDFs no próprio dispositivo.
- Não há login, banco compartilhado nem armazenamento de PDFs em nuvem. Não use esta versão como repositório institucional de documentos pessoais até conectar autenticação, banco de dados e armazenamento privado.
- A extração de texto é uma primeira camada de leitura e exige conferência; PDFs digitalizados exigem OCR. A interface deixa registros incertos pendentes em vez de inventar dados.
- Para produção, conectar banco persistente com controle por usuário, armazenamento privado de arquivos, trilha de auditoria e OCR no servidor. A regra de 75% deve ser configurada em unidade coerente com o regimento e a carga horária da rede.
- Os alertas de risco são indicativos. O resultado final depende de dados completos, calendário e normas institucionais.
- Ao configurar um componente, informe o total de aulas/encontros do semestre e defina o tratamento das faltas justificadas conforme o regimento. Se a duração das aulas variar, use a carga horária real em vez de contar encontros como equivalentes.

A exportação para PDF usa a opção de impressão do navegador, permitindo salvar a tabela filtrada. A extração OCR roda no navegador quando a página do PDF não contém texto selecionável.

## Pastas mensais

A árvore `relatorios/2026/2-semestre/` já contém as pastas de julho a dezembro, cada uma subdividida pelas cinco turmas cadastradas. Os diretórios são apenas uma organização de projeto: os PDFs reais são enviados pela tela **Importações**. O arquivo `.gitignore` impede que PDFs adicionados nessas pastas sejam enviados ao repositório. Não publique relatórios com dados pessoais em diretórios estáticos da Vercel.

Na área **Alunos**, os resultados são agrupados por turma e componente curricular. Dentro de cada grupo, os alertas prioritários aparecem primeiro; frequências abaixo de 75% em dados parciais são sinalizadas como atenção parcial, sem indicar reprovação final.
