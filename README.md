# CalculadoraDescontos

Grupo

Anthony Rafael Braga Magalhães – RA: 4251924039
Guilherme de Oliveira Navais – RA: 4251923674
Lucas Paiva Magalhães – RA: 4251925101
Luca Fernandes – RA: 4251924436
------//-------//-------//--------///------//-----

Projeto da disciplina de Garantia da Qualidade de Software que demonstra testes
unitários com xUnit em .NET 10, usando testes parametrizados.

## Estrutura

- `CalculadoraDescontos.App`: código de produção (`DescontoService`)
- `CalculadoraDescontos.Tests`: testes unitários com xUnit

## Requisitos

- [.NET 10 SDK](https://dotnet.microsoft.com/download)

## Como executar os testes

Clone o repositório, entre na pasta e rode:

```bash
git clone https://github.com/lucavaladares45/calculadora-descontos-xunit.git
cd calculadora-descontos-xunit
dotnet test
```

Cada `[InlineData]` aparece como um teste individual no resultado.

## Diferença entre [Fact] e [Theory]

| | `[Fact]` | `[Theory]` |
|---|---|---|
| O que é | Teste único, sem parâmetros | Teste parametrizado |
| Execuções | Uma vez | Uma vez para cada `[InlineData]` |
| Dados | Fixos dentro do método | Vêm dos parâmetros do método |
| Quando usar | Cenário único e fixo | Mesma lógica com vários valores de entrada |

Exemplo de `[Theory]` usado neste projeto:

```csharp
[Theory]
[InlineData(2, "BRONZE")]
[InlineData(7, "PRATA")]
[InlineData(15, "OURO")]
public void ObterCategoriaCliente_DeveRetornarCategoriaCorreta(int totalCompras, string esperado)
{
    Assert.Equal(esperado, _service.ObterCategoriaCliente(totalCompras));
}
```

Em vez de escrever três métodos quase iguais, um único método roda três vezes.

## Licença

Distribuído sob a licença MIT. Veja o arquivo `LICENSE`.