# CNPJValidatorV2

Uma biblioteca C# moderna para validação, formatação e cálculo de dígito verificador de CNPJs.

## ✨ Funcionalidades

- ✅ Validação completa de CNPJs com e sem formatação
- 🧮 Cálculo automático dos dígitos verificadores (DV)
- 🧼 Sanitização de entrada (remove caracteres inválidos)
- 🧾 Formatação no padrão `00.000.000/0000-00`

---

## 🚀 Instalação

Instale via NuGet:

```bash
dotnet add package CNPJValidatorV2
```

---

## 🔍 Exemplo de uso

```csharp
using CNPJValidatorV2.Core;

// Verifica se um CNPJ é válido
bool valido = CnpjValidator.IsValid("12.345.678/0001-95"); // true
bool valido = CnpjValidator.IsValid("12.ABC.345/01DE-35"); // true
bool valido = CnpjValidator.IsValid("12.aBC.345/01DE-35"); // false - somente letras maiúsculas são aceitas

// Sanitiza um CNPJ
string cnpj = "12.345.678/0001-95".SanitizeCnpj(); // "12345678000195"

// Formata um CNPJ simples
string formatado = "12345678000195".FormatCnpj(); // "12.345.678/0001-95"

// Calcula o DV a partir de um número base (com ou sem letras)
string cnpjComDV = CNPJValidator.CalculateDv("12ABC34501DE"); // "12ABC34501DE35"

// Calcula e já formata
string formatadoComDV = CNPJValidator.CalculateDv("12ABC34501DE").FormatCnpj(); // "12.ABC.345/01DE-35"
```

---

## ✅ Testes automatizados

Este projeto possui testes com [xUnit](https://xunit.net/) que cobrem:

- Validação de CNPJs reais
- Cálculo correto dos dígitos verificadores
- Detecção de CNPJs malformados
- Comparações com valores esperados
- Testes de formatação

Execute os testes com:

```bash
dotnet test
```

---

## ⚠️ Erros tratados

O método `CalculateDv` lança exceção se o CNPJ tiver menos de 12 caracteres alfanuméricos:

```csharp
Assert.Throws<ArgumentException>(() => CNPJValidator.CalculateDv("123"));
```

---

## 📄 Licença

Este projeto está licenciado sob a licença MIT.

© 2025 Tiago Ávila Saldanha
