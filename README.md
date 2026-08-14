# Código completo — aula de POO, UML e Java

## Compatibilidade da versão portátil

A versão portátil publicada na seção **Releases** inclui o **Eclipse Temurin
JDK 17** na pasta `java`. Os programas usam diretamente esse Java, sem procurar
outra instalação no computador.

Por causa do tamanho do JDK, a pasta `java` está no `.gitignore` e não acompanha
um clone comum do repositório nem o botão **Code > Download ZIP**. Quem não
possui Java instalado deve baixar o ZIP portátil disponibilizado em
**Releases**.

Para usar esta cópia portátil, o computador precisa ter:

- Windows x64 (64 bits, processador Intel ou AMD);
- permissão para executar arquivos `.bat` e `.exe` dentro da pasta do projeto.

Não é necessário:

- instalar Java;
- possuir outro JDK ou JRE;
- configurar `JAVA_HOME`;
- alterar o `PATH`;
- possuir acesso à internet depois que o projeto for baixado.

Esta cópia do JDK **não é compatível** com Windows 32 bits, Windows ARM, Linux
ou macOS. Para esses sistemas, seria necessário incluir o JDK correspondente.

## Forma mais simples de executar

Destas instruções em diante, considera-se que foi baixado e extraído o ZIP
portátil da seção **Releases**, incluindo a pasta `java`.

Dê dois cliques em `executar.bat` e escolha no menu qual exemplo deseja
compilar e executar.

Também é possível escolher o exemplo pelo Prompt de Comando. Abra o terminal
na pasta do projeto e use um dos comandos abaixo:

```bat
executar.bat visita1
executar.bat visita2
executar.bat visita3
executar.bat visita4
executar.bat visita5
executar.bat visita6
executar.bat visita7
executar.bat visita8
executar.bat visita9
executar.bat visita10
executar.bat visita11
executar.bat nucleo1
executar.bat nucleo2
executar.bat nucleo3
```

O `executar.bat` sempre utiliza estes executáveis locais:

```text
java\bin\javac.exe
java\bin\java.exe
```

## Comandos manuais usando o Java portátil

No **Prompt de Comando (CMD)**, execute estas duas linhas para compilar e
iniciar a `visita1`:

```bat
if not exist build-portatil mkdir build-portatil
java\bin\javac.exe -encoding UTF-8 -d build-portatil visita1\*.java
java\bin\java.exe -Dfile.encoding=UTF-8 -cp build-portatil visita1.Aplicacao
```

Para escolher outro exemplo, substitua `visita1` pelo pacote desejado. Por
exemplo, para executar `nucleo1`:

```bat
if not exist build-portatil mkdir build-portatil
java\bin\javac.exe -encoding UTF-8 -d build-portatil nucleo1\*.java
java\bin\java.exe -Dfile.encoding=UTF-8 -cp build-portatil nucleo1.Aplicacao
```

No **PowerShell**, o equivalente para `visita1` é:

```powershell
New-Item -ItemType Directory -Force .\build-portatil | Out-Null; $fontes = Get-ChildItem .\visita1\*.java | ForEach-Object FullName; & .\java\bin\javac.exe -encoding UTF-8 -d .\build-portatil $fontes; if ($LASTEXITCODE -eq 0) { & .\java\bin\java.exe "-Dfile.encoding=UTF-8" -cp .\build-portatil visita1.Aplicacao }
```

O argumento `-encoding UTF-8` faz o compilador interpretar corretamente os
arquivos-fonte. O argumento `-Dfile.encoding=UTF-8` deve permanecer no comando
de execução para preservar acentos e caracteres em português.

## Publicação no GitHub

O JDK portátil ocupa aproximadamente 303 MB, e o arquivo `java/lib/modules`
sozinho ultrapassa 100 MB. Por isso, a pasta `java` completa não pode ser
publicada diretamente em um repositório GitHub comum.

A distribuição recomendada é:

1. Manter no repositório os códigos-fonte, o `README.md` e o `executar.bat`.
2. Criar um ZIP do projeto completo, incluindo a pasta `java`.
3. Publicar esse ZIP como arquivo de uma **GitHub Release**.
4. Orientar o usuário a baixar o ZIP pela seção **Releases**, extrair todo o
   conteúdo e abrir `executar.bat`.

O botão **Code > Download ZIP** baixa o conteúdo normal do repositório, não o
arquivo portátil anexado à Release. Para receber o Java incluído, o usuário
deve baixar especificamente o arquivo disponibilizado em **Releases**.

Git LFS também pode armazenar os arquivos grandes, mas adiciona configuração,
cotas e uma dependência extra para quem clona o repositório. Para esta aula, a
Release com um único ZIP portátil é a alternativa mais simples.
