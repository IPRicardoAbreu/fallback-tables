Tabelas de Contigencia (fallback-tables)
===============

Ajuda o varejista a fazer cotações de frete em caso que a API da intelipost estiver lento ou com downtime. 

Como funciona?
===============

Este recurso permite que uma cotação seja feita em modo offline, quando houver perda ou instabilidade de conexão com a Intelipost. Na cotação de contingência será utilizada uma tabela com base em ranges de CEP. No seu processo de integração com a Intelipost, aconselhamos a implantar este processo para protege-los de quaisquer eventuais problemas.

Utilizaremos um arquivo json com os valores para calculo de contingencia. Deixamos alguns modelos prontos para serem utilizado.

O ideal seria converter este arquivo em um objeto e salva-lo no cache da aplicação, para que desta forma este arquivo seja carregado apenas uma vez, não todas as vezes que for feita uma cotação de contingencia, por motivos de performance.

Para realizar a identificação de qual range de CEP e PESO condizem com as informações da cotação a ser realizada, efetuar uma busca binaria no objeto salvo em cache no primeiro passo.

Após a identificação do objeto que condiz com as informações fornecidas, sugerimos que o preço final do frete seja calculado da seguinte maneira: Exemplo do calculo: ((invoice_total_value*(price_percent/100))+shipping_cost)


