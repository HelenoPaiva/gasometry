# Gasometria no intraoperatório

Aplicativo para apoiar a interpretação de gasometrias em adultos, com análise acidobásica, anion gap, abordagem físico-química simplificada e comparação de alpha-stat/pH-stat. Desenvolvido em um único arquivo HTML, com interface em português e inglês e temas claro e escuro.

**[Abrir aplicativo](https://helenopaiva.github.io/gasometry/)** · **[Repositório](https://github.com/HelenoPaiva/gasometry)**

Versão documentada: **1.2.3**, de 2 de novembro de 2026.

> Ferramenta de apoio ao raciocínio clínico e ao ensino. Protótipo não validado clinicamente: os resultados exigem revisão profissional e integração ao contexto do paciente. O aplicativo não fornece doses nem prescrição automática.

## Como usar

1. Abra o aplicativo no navegador ou baixe `index.html` e abra o arquivo localmente.
2. Selecione a origem da amostra e o tipo de ventilação. Informe **pH e PCO₂**, os únicos valores obrigatórios.
3. Preencha os dados disponíveis. Se deixar o HCO₃⁻ atual vazio, o aplicativo o estima por Henderson–Hasselbalch na base de 37 °C.
4. Acrescente o contexto clínico e, quando necessário, os dados de temperatura.
5. Clique em **Interpretar**. Revise a interpretação, os cálculos e os próximos passos sugeridos.
6. Use as opções de copiar ou imprimir para obter o relatório. Na impressão, também é possível salvar em PDF pelo navegador. Clique em **Limpar** antes de iniciar uma nova avaliação.

O formulário aceita ponto ou vírgula decimal. Deixe valores desconhecidos em branco; zero é interpretado como um valor informado. Ao editar os dados, o resultado anterior é invalidado até uma nova análise.

## Funcionalidades

- Interpretação do pH e dos componentes metabólico e respiratório, com comparação entre compensação esperada e valor observado quando aplicável.
- Anion gap sem potássio, correção pela albumina, delta gap e razão delta quando os critérios de cálculo são atendidos. O basal e o limite superior do AG podem ser ajustados ao laboratório.
- Avaliação da diferença Na⁺ − Cl⁻ e decomposição **Stewart light**, disponível com sódio, cloro, albumina e SBE/BEecf. Essa abordagem não corresponde a um cálculo completo de SID/SIG.
- Integração de lactato, eletrólitos, oxigenação e contexto clínico às orientações. Relação PaO₂/FiO₂ quando aplicável.
- Módulo opcional de temperatura com alpha-stat/pH-stat e identificação de circulação extracorpórea (CEC).
- Alertas de valores relevantes e de inconsistências nos dados, com cálculos, método e referências consultáveis.
- Relatório para cópia e impressão; nove exemplos simulados, identificados como material de estudo.
- Interface responsiva, teclado decimal em dispositivos compatíveis, alternância PT/EN e tema claro/escuro.

## Dados e unidades

| Dados | Unidade ou convenção |
| --- | --- |
| pH | Sem unidade |
| PCO₂ e PO₂ | mmHg |
| HCO₃⁻ atual, CO₂ total, SBE/BEecf | mmol/L; usar SBE/BEecf, não BE(B) |
| Na⁺, K⁺, Cl⁻, cálcio ionizado, lactato, Cl⁻ urinário | mmol/L; cálcio ionizado, não cálcio total |
| Albumina | g/dL; 40 g/L corresponde a 4 g/dL |
| Glicose | mg/dL |
| FiO₂ | Porcentagem; informar 40 para 40%, não 0,40 |
| Temperatura central | °C, no momento da coleta |
| AG basal e limite superior | mEq/L, sem K⁺ |

Use resultados de amostras contemporâneas. O CO₂ total sérico, quando preenchido, substitui o HCO₃⁻ somente no AG e nos deltas. Diferenças relevantes entre esses valores limitam a classificação automática.

## Alpha-stat e pH-stat

Abra **Temperatura · alpha-stat / pH-stat**, informe a temperatura central e indique se o pH e a PCO₂ foram reportados a **37 °C** ou **já corrigidos à temperatura do paciente**. Selecione a estratégia utilizada ou apenas compare as referências; marque CEC quando aplicável.

O módulo apresenta os valores informados e o par estimado na outra base de temperatura, além de uma comparação conceitual das estratégias. Essa análise aparece **ao final da interpretação, imediatamente antes de “Próximos passos”**, e integra os relatórios.

- A conversão se refere à mesma amostra e não prevê a resposta a uma intervenção.
- As estimativas usam as equações descritas no manual RAPIDPoint 500e, citado no aplicativo. Métodos dos gasômetros podem diferir; prefira os pares reportados pelo equipamento quando disponíveis.
- O módulo converte somente **pH e PCO₂**. HCO₃⁻, SBE e PO₂ devem ser informados na base de **37 °C**.
- A faixa operacional de entrada é **15–42 °C**; ela não representa uma faixa de validação clínica.
- Selecionar uma estratégia não a prescreve nem confirma sua aplicação. As referências de pH 7,40 e PaCO₂ 40 mmHg são conceituais, não metas individualizadas.
- Em CEC e nos cenários de pH-stat contemplados pelo código, a análise convencional recebe ressalvas e não aplica automaticamente as regras habituais de compensação. Em CEC, a relação PaO₂/FiO₂ também é omitida.

## Alcance e limitações

A estrutura de referência é voltada a **adultos**. Amostras venosas recebem análise limitada e não são usadas para avaliar oxigenação arterial. O aplicativo não constitui protocolo pediátrico, obstétrico, de perfusão, ECMO, hipotermia profunda ou intoxicações.

As hipóteses são geradas por regras explícitas. A gasometria isolada não estabelece etiologia, volemia, choque, SDRA ou necessidade de transfusão. Fórmulas de compensação, valores de referência e limiares operacionais têm limitações, descritas em **Método, alcance e limites**. As orientações servem para organizar a próxima avaliação clínica.

## Execução e privacidade

Todo o cálculo ocorre no navegador. O aplicativo não usa backend, APIs de análise, telemetria ou bibliotecas externas. HTML, CSS e JavaScript estão contidos em `index.html`; não há etapa de instalação ou compilação.

Os dados digitados permanecem na memória da aba e são removidos ao limpar ou recarregar. Apenas idioma e tema podem ser lembrados via `localStorage`. Copiar ou imprimir um relatório cria uma saída sob controle do usuário, que deve ser revisada antes de ser registrada ou compartilhada.

Para uso offline, baixe `index.html` e abra a cópia local em um navegador com JavaScript habilitado. A versão hospedada requer internet para o carregamento inicial; reabri-la offline depende do navegador. Os links do GitHub e das referências precisam de conexão.

## Arquivos e atualização no GitHub

| Arquivo | Conteúdo |
| --- | --- |
| `index.html` | Aplicativo completo |
| `README.md` | Documentação de uso |
| `LICENSE` | Licença MIT do projeto |

Para atualizar pelo site do GitHub, envie `index.html` e `README.md` à raiz do repositório, substituindo os arquivos correspondentes e mantendo `LICENSE`. Use a branch e a pasta configuradas como origem do GitHub Pages. Depois da publicação, confira a versão indicada no rodapé do aplicativo.

## Referências

A lista completa, com os vínculos entre referências e orientações, está em **Referências clínicas** no aplicativo. Entre as bases utilizadas estão:

- Park, Cave e Freebairn. [Metabolic acidosis in anaesthesia and critical care](https://pmc.ncbi.nlm.nih.gov/articles/PMC10874758/). *BJA Education*, 2024.
- Park e Sidebotham. [Metabolic alkalosis and mixed acid–base disturbance in anaesthesia and critical care](https://pmc.ncbi.nlm.nih.gov/articles/PMC10028421/). *BJA Education*, 2023.
- Pippalapalli e Lumb. [The respiratory system and acid–base disorders](https://pmc.ncbi.nlm.nih.gov/articles/PMC10201398/). *BJA Education*, 2023.
- Wahba et al. [2024 EACTS/EACTAIC/EBCP Guidelines on cardiopulmonary bypass in adult cardiac surgery](https://doi.org/10.1093/ejcts/ezae354). *European Journal of Cardio-Thoracic Surgery*, 2025.
- Siemens Healthineers. [RAPIDPoint 500e Operator’s Guide](https://doclib.siemens-healthineers.com/rest/v1/view?document-id=858615). Rev. E, 2023, seção *Patient Temperature Correction*, p. F-17.

## Contribuições e licença

Sugestões e relatos de problemas podem ser enviados pelas [Issues](https://github.com/HelenoPaiva/gasometry/issues). Para reproduzir um problema, informe a versão, o navegador e um exemplo fictício, sem dados identificáveis de pacientes.

Projeto de **Heleno Paiva**, distribuído sob a [licença MIT](LICENSE).
