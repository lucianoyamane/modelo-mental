# Parse, Don't Validate

## Contexto

Sistemas frequentemente recebem dados externos por APIs, eventos, arquivos ou mensagens. Carregar esses dados como estruturas parcialmente válidas pelo domínio aumenta a chance de regras defensivas espalhadas, estados inválidos e acoplamento com contratos externos.

## Princípio

Transforme dados externos em tipos válidos do domínio na borda do sistema.

Validar apenas rejeita ou aceita uma estrutura. Fazer parsing cria uma representação interna mais segura, explícita e alinhada ao domínio.

## Decisão

Ao receber dados externos:

* trate o contrato externo como entrada instável;
* valide e traduza na borda;
* crie tipos internos que não representem estados inválidos;
* impeça que DTOs, payloads ou schemas externos contaminem o núcleo do domínio.

## Exemplo conceitual

```text
Mensagem Externa
        |
        v
Camada de Parsing e Tradução
        |
        v
Objeto de Domínio Válido
```

## Trade-offs

* Aumenta código de tradução nas bordas.
* Reduz condicionais defensivas no domínio.
* Melhora testabilidade das regras centrais.
* Exige disciplina para não reutilizar modelos externos por conveniência.

## Relações

* [Source e Translation](../04-integracao/source-e-translation.md)
* [Arquitetura Fonte da Verdade](../04-integracao/arquitetura-fonte-da-verdade.md)
* [Máquinas de Estado](./finite-state-machine.md)
