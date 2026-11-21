# Habbinho gamedata

Este repositório mantém a documentação de procedência e a receita de empacotamento dos dados que Octane e Polaris carregam. A árvore legada já presente neste checkout tem procedência por revisar. Prepare a distribuição em uma pasta vazia, incluindo somente dados próprios ou com autorização que cubra a publicação e o uso no hotel.

## Preparar uma versão

1. Registre as origens e permissões dos arquivos em uma cópia do [modelo de procedência](PROVENANCE.md). Inclua as atribuições e os textos que a licença exigir em `licenses/` na pasta preparada.
2. Organize as pastas `config/`, `clothes/`, `furniture/` e as demais conforme consumidas pelo cliente. Coloque ícones em uma pasta real `icons/` se usados. As configurações exigidas são `EffectMap.json`, `ExternalTexts.json`, `FigureData.json`, `FigureMap.json`, `FurnitureData.json`, `HabboAvatarActions.json`, `ProductData.json` e `UITexts.jsonc`, em `config/`. Dados de configuração e textos de terceiros também precisam de permissão aplicável.
3. Gere o pacote com Python 3.9+ e revise a lista de arquivos. O comando recusa a raiz de um checkout, links, arquivos ocultos e entradas fora das pastas esperadas. Para a mesma árvore, a ordem e os metadados normalizados permitem comparar builds por SHA-256.

```bash
./scripts/pack --reviewed /caminho/gamedata-preparado /caminho/releases/gamedata-v0.1.0
tar -tzf /caminho/releases/gamedata-v0.1.0/gamedata.tar.gz
(cd /caminho/releases/gamedata-v0.1.0 && sha256sum -c gamedata.tar.gz.sha256)
```

4. Valide com as versões de Octane e Polaris selecionadas na stack, incluindo conexão, entrada em um quarto e os assets requeridos pelo avatar e pelo catálogo. A validação do script cobre os caminhos e a sintaxe das configurações. A compatibilidade de IDs, formatos, URLs e o funcionamento do jogo se verificam na stack.
5. Anexe `gamedata.tar.gz` e `gamedata.tar.gz.sha256` à release `gamedata-v0.1.0` e registre a URL versionada e o SHA-256 no `hotel-stack`. Use uma nova tag para qualquer alteração no pacote. Preserve as atribuições exigidas pela licença ao disponibilizar os assets.

Um conjunto pequeno e próprio pode servir como fixture de configuração e entrega local. Use uma pasta preparada separada e siga o mesmo comando. A entrega para jogadores depende de um conjunto autorizado e jogável.
