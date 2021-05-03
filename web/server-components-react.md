# Server Components React

Como foi apresentado no vídeo, o recurso ainda é experimental; não existe documentação real.

Os componentes do servidor nos permitirá carregar componentes do backend. Como os componentes já foram renderizados no backend, eles podem ser integrados perfeitamente ao aplicativo em execução. É um pouco como a renderização do lado do servidor, mas funciona de forma diferente.

Achei semelhante ao que o pessoal do Next.js usa (getInitialProps), onde os componentes do servidor podem buscar dados e passá-los para componentes frontend.

Vejo, que, ao contrário do SSR clássico, os componentes do servidor são um pouco mais dinâmicos. Quando buscamos um dado do servidor durante a execução do aplicativo, o estado do cliente não é perdido e funciona de forma tecnicamente diferente. Com o SSR, o nosso código JS é processado em HTML no servidor. Isso cria um modelo HTML, que é a parte visível de nossa página da web. Com isso, enviamos ao cliente o HTML e o JS usado para interatividade.

Os componentes do servidor são incluídos dinamicamente no aplicativo e transmitidos de forma especial. Qual seria a vantagem dos componentes do servidor?

## Zero-Bundle-Size-Components

Show! O mundo JS está lotado de enormes libs. Para o desempenho do aplicativo e, portanto, para o usuário, isso é, obviamente, muito ruim - todo o código é enviado para o frontend.

Graças aos componentes do servidor, podemos poupar nosso frontend desse código também.

Como exemplo, a equipe React mostra o código que importa uma biblioteca para renderizar Markdown.
Claro, não queremos enviar tantos códigos para o usuário - isso custa tempo e largura de banda. Além disso, o componente não tem interatividade alguma - ele apenas renderiza Markdown.

### Solução: componente de servidor.

Portanto, em vez de enviar todo o código da biblioteca Markdown para o cliente, o cliente obtém apenas o resultado renderizado.
Em resumo, os componentes do servidor não afetam o tamanho do pacote de nosso aplicativo frontend. O código é executado apenas no backend e não é visível para o usuário.

Isso deve estar claro agora, depois que todo o código React estiver sendo executado em nosso backend. Assim, semelhante ao Next.js, podemos acessar o backend, embora no caso do Next apenas por meio de feature para bancos de dados, sistema de arquivos e outros.

Além de **react-pg** e **react-fetch**, **react-fs** é um deles.
Isso mesmo, **“fs”**, que significa o sistema de arquivos.

**Sim, podemos acessar o sistema de arquivos de nosso backend com React.js.** Isso é Maravilhoso!
