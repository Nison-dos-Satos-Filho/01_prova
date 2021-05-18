01\_avaliação
================
Nilson dos Santos Filho </br>
08/05/2021

------------------------------------------------------------------------

I Sobre o dataset “peixes\_rio\_madeira.csv”</br> **Questão 01**

**a**

``` r
dados_prm <- read_csv("dados/brutos/peixes_rio_madeira.csv")
```

    ## 
    ## -- Column specification --------------------------------------------------------
    ## cols(
    ##   .default = col_character(),
    ##   id = col_double(),
    ##   data = col_datetime(format = ""),
    ##   mes = col_double(),
    ##   ano = col_double(),
    ##   local = col_double(),
    ##   cp_cm = col_double(),
    ##   peso_g = col_double()
    ## )
    ## i Use `spec()` for the full column specifications.

``` r
dados_prm %>% View()
```

``` r
dados_prm %>% 
  glimpse()
```

    ## Rows: 99,370
    ## Columns: 21
    ## $ id                   <dbl> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15~
    ## $ tipo_campanha        <chr> "Mensal", "Mensal", "Mensal", "Mensal", "Mensal",~
    ## $ campanha             <chr> "Mensal 1", "Mensal 1", "Mensal 1", "Mensal 1", "~
    ## $ data                 <dttm> 2010-05-03, 2010-05-03, 2010-05-03, 2010-05-03, ~
    ## $ mes                  <dbl> 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5~
    ## $ ano                  <dbl> 2010, 2010, 2010, 2010, 2010, 2010, 2010, 2010, 2~
    ## $ ciclo_hidrologico    <chr> "Vazante", "Vazante", "Vazante", "Vazante", "Vaza~
    ## $ bacia                <chr> "Rio Madeira", "Rio Madeira", "Rio Madeira", "Rio~
    ## $ ambiente             <chr> "Tributário", "Tributário", "Tributário", "Tribut~
    ## $ local                <dbl> 1, 1, 1, 1, 1, 2, 2, 2, 3, 3, 3, 3, 4, 4, 5, 5, 5~
    ## $ ponto                <chr> "Tribut 1", "Tribut 1", "Tribut 1", "Tribut 1", "~
    ## $ especie              <chr> "Auchenipterichthys thoracatus", "Aucheniptericht~
    ## $ genero               <chr> "Auchenipterichthys", "Auchenipterichthys", "Auch~
    ## $ familia              <chr> "Auchenipteridae", "Auchenipteridae", "Auchenipte~
    ## $ ordem                <chr> "Siluriformes", "Siluriformes", "Siluriformes", "~
    ## $ nome_comum           <chr> "Cangati/Cachorro-de-padre", "Cangati/Cachorro-de~
    ## $ cp_cm                <dbl> 12.0, 11.5, 11.0, 26.5, 27.0, 20.0, 11.0, 16.0, 8~
    ## $ peso_g               <dbl> 35, 35, 25, 265, 160, 130, 25, 65, 15, 250, 465, ~
    ## $ sexo                 <chr> "Fêmea", "Macho", "Fêmea", "Fêmea", "Não coletado~
    ## $ estadio_de_maturacao <chr> "Imaturo", "Imaturo", "Imaturo", "Repouso", "Não ~
    ## $ habito_alimentar     <chr> "Onívoro", "Onívoro", "Onívoro", "Carnívoro", "Ca~

``` r
dados_prm %>% 
  group_by(ordem) %>% 
  summarise(n = n()) %>% 
  arrange(n)
```

    ## # A tibble: 12 x 2
    ##    ordem                  n
    ##    <chr>              <int>
    ##  1 Lepidosireniformes     2
    ##  2 Pleuronectiformes      2
    ##  3 Beloniformes           5
    ##  4 Não identificado      17
    ##  5 Myliobatiformes       41
    ##  6 Osteoglossiformes    433
    ##  7 Gymnotiformes        693
    ##  8 Acanthuriformes     1602
    ##  9 Cichliformes        1947
    ## 10 Clupeiformes        2821
    ## 11 Siluriformes       27451
    ## 12 Characiformes      64356

**b**</br>A ordem de peixe mais identificada foi o Characiformes e foram
feitas 12 observações.

**c**</br> Não foram identificados 17 peixes.

``` r
dados_prm %>% 
  distinct(ordem)
```

    ## # A tibble: 12 x 1
    ##    ordem             
    ##    <chr>             
    ##  1 Siluriformes      
    ##  2 Characiformes     
    ##  3 Cichliformes      
    ##  4 Clupeiformes      
    ##  5 Acanthuriformes   
    ##  6 Não identificado  
    ##  7 Gymnotiformes     
    ##  8 Osteoglossiformes 
    ##  9 Myliobatiformes   
    ## 10 Beloniformes      
    ## 11 Pleuronectiformes 
    ## 12 Lepidosireniformes

``` r
dados_prm %>% 
  filter(ordem == "Não identificado")
```

    ## # A tibble: 17 x 21
    ##       id tipo_campanha campanha data                  mes   ano ciclo_hidrologi~
    ##    <dbl> <chr>         <chr>    <dttm>              <dbl> <dbl> <chr>           
    ##  1    53 Mensal        Mensal 1 2010-05-05 00:00:00     5  2010 Vazante         
    ##  2    59 Mensal        Mensal 1 2010-05-06 00:00:00     5  2010 Vazante         
    ##  3   281 Mensal        Mensal 1 2010-05-12 00:00:00     5  2010 Vazante         
    ##  4   327 Mensal        Mensal 2 2010-06-01 00:00:00     6  2010 Vazante         
    ##  5   717 Mensal        Mensal 2 2010-06-07 00:00:00     6  2010 Vazante         
    ##  6   947 Mensal        Mensal 2 2010-06-11 00:00:00     6  2010 Vazante         
    ##  7   964 Mensal        Mensal 2 2010-06-11 00:00:00     6  2010 Vazante         
    ##  8  1097 Mensal        Mensal 3 2010-07-03 00:00:00     7  2010 Seca            
    ##  9  1518 Mensal        Mensal 3 2010-07-08 00:00:00     7  2010 Seca            
    ## 10  1621 Mensal        Mensal 4 2010-08-02 00:00:00     8  2010 Seca            
    ## 11  1688 Mensal        Mensal 4 2010-08-03 00:00:00     8  2010 Seca            
    ## 12  1727 Mensal        Mensal 4 2010-08-03 00:00:00     8  2010 Seca            
    ## 13  1800 Mensal        Mensal 4 2010-08-05 00:00:00     8  2010 Seca            
    ## 14  1826 Mensal        Mensal 4 2010-08-05 00:00:00     8  2010 Seca            
    ## 15  2381 Mensal        Mensal 4 2010-08-09 00:00:00     8  2010 Seca            
    ## 16  2408 Mensal        Mensal 4 2010-08-09 00:00:00     8  2010 Seca            
    ## 17 20211 Bimestral     Bimestr~ 2012-08-01 00:00:00     8  2012 Seca            
    ## # ... with 14 more variables: bacia <chr>, ambiente <chr>, local <dbl>,
    ## #   ponto <chr>, especie <chr>, genero <chr>, familia <chr>, ordem <chr>,
    ## #   nome_comum <chr>, cp_cm <dbl>, peso_g <dbl>, sexo <chr>,
    ## #   estadio_de_maturacao <chr>, habito_alimentar <chr>

**Questão 2**

``` r
dados_prm %>% 
  distinct(bacia)
```

    ## # A tibble: 3 x 1
    ##   bacia      
    ##   <chr>      
    ## 1 Rio Madeira
    ## 2 Rio Mamoré 
    ## 3 Rio Guaporé

``` r
dados_prm %>% 
select(ordem, peso_g)
```

    ## # A tibble: 99,370 x 2
    ##    ordem         peso_g
    ##    <chr>          <dbl>
    ##  1 Siluriformes      35
    ##  2 Siluriformes      35
    ##  3 Siluriformes      25
    ##  4 Characiformes    265
    ##  5 Siluriformes     160
    ##  6 Characiformes    130
    ##  7 Siluriformes      25
    ##  8 Characiformes     65
    ##  9 Cichliformes      15
    ## 10 Characiformes    250
    ## # ... with 99,360 more rows

``` r
dados_prm %>% 
  summarise(
    media_peso = mean(peso_g)
  )
```

    ## # A tibble: 1 x 1
    ##   media_peso
    ##        <dbl>
    ## 1         NA

``` r
dados_prm %>% 
  group_by(ordem) %>% 
  drop_na() %>% 
  summarise(
    media_peso = mean(peso_g)
  )
```

    ## # A tibble: 11 x 2
    ##    ordem             media_peso
    ##    <chr>                  <dbl>
    ##  1 Acanthuriformes        556. 
    ##  2 Beloniformes            13.6
    ##  3 Characiformes          165. 
    ##  4 Cichliformes           210. 
    ##  5 Clupeiformes           264. 
    ##  6 Gymnotiformes          150. 
    ##  7 Myliobatiformes       1878. 
    ##  8 Não identificado       494. 
    ##  9 Osteoglossiformes      595. 
    ## 10 Pleuronectiformes      156  
    ## 11 Siluriformes           273.

``` r
dados_prm %>% 
  group_by(ordem) %>% 
  drop_na() %>% 
  summarise(
    Desvio_p = sd(peso_g)
  )
```

    ## # A tibble: 11 x 2
    ##    ordem             Desvio_p
    ##    <chr>                <dbl>
    ##  1 Acanthuriformes      459. 
    ##  2 Beloniformes          15.5
    ##  3 Characiformes        236. 
    ##  4 Cichliformes         283. 
    ##  5 Clupeiformes         272. 
    ##  6 Gymnotiformes        206. 
    ##  7 Myliobatiformes     1871. 
    ##  8 Não identificado    1078. 
    ##  9 Osteoglossiformes   1821. 
    ## 10 Pleuronectiformes    187. 
    ## 11 Siluriformes         933.

**a**</br>Pelos dados calculados acima: A média de variabilidade mais
adequada é Coeficiente de Variação.

**b**</br>Pelos dados calculados abaixo: A ordem de peixes que tem
distribuição de peso mais homogênia é Acanthuriformes.

``` r
dados_prm %>% 
  group_by(ordem) %>% 
  drop_na() %>% 
  summarise(
    cv = (sd(peso_g)/mean(peso_g)) * 100
  )
```

    ## # A tibble: 11 x 2
    ##    ordem                cv
    ##    <chr>             <dbl>
    ##  1 Acanthuriformes    82.5
    ##  2 Beloniformes      114. 
    ##  3 Characiformes     143. 
    ##  4 Cichliformes      135. 
    ##  5 Clupeiformes      103. 
    ##  6 Gymnotiformes     138. 
    ##  7 Myliobatiformes    99.6
    ##  8 Não identificado  218. 
    ##  9 Osteoglossiformes 306. 
    ## 10 Pleuronectiformes 120. 
    ## 11 Siluriformes      342.

**Questão 3**

``` r
dados_prm %>% 
  distinct(sexo)
```

    ## # A tibble: 4 x 1
    ##   sexo        
    ##   <chr>       
    ## 1 Fêmea       
    ## 2 Macho       
    ## 3 Não coletado
    ## 4 fêmea

``` r
dados_prm %>% 
  mutate(
   sexo_recode = recode(
    sexo,
    "Fêmea" = "Fêmea",
    "Macho" = "Macho",
    "fêmea" = "Fêmea",
    "Não coletado" = "Não coletado"
   ) 
  ) 
```

    ## # A tibble: 99,370 x 22
    ##       id tipo_campanha campanha data                  mes   ano ciclo_hidrologi~
    ##    <dbl> <chr>         <chr>    <dttm>              <dbl> <dbl> <chr>           
    ##  1     1 Mensal        Mensal 1 2010-05-03 00:00:00     5  2010 Vazante         
    ##  2     2 Mensal        Mensal 1 2010-05-03 00:00:00     5  2010 Vazante         
    ##  3     3 Mensal        Mensal 1 2010-05-03 00:00:00     5  2010 Vazante         
    ##  4     4 Mensal        Mensal 1 2010-05-03 00:00:00     5  2010 Vazante         
    ##  5     5 Mensal        Mensal 1 2010-05-03 00:00:00     5  2010 Vazante         
    ##  6     6 Mensal        Mensal 1 2010-05-03 00:00:00     5  2010 Vazante         
    ##  7     7 Mensal        Mensal 1 2010-05-03 00:00:00     5  2010 Vazante         
    ##  8     8 Mensal        Mensal 1 2010-05-03 00:00:00     5  2010 Vazante         
    ##  9     9 Mensal        Mensal 1 2010-05-03 00:00:00     5  2010 Vazante         
    ## 10    10 Mensal        Mensal 1 2010-05-03 00:00:00     5  2010 Vazante         
    ## # ... with 99,360 more rows, and 15 more variables: bacia <chr>,
    ## #   ambiente <chr>, local <dbl>, ponto <chr>, especie <chr>, genero <chr>,
    ## #   familia <chr>, ordem <chr>, nome_comum <chr>, cp_cm <dbl>, peso_g <dbl>,
    ## #   sexo <chr>, estadio_de_maturacao <chr>, habito_alimentar <chr>,
    ## #   sexo_recode <chr>

``` r
dados_prm %>% 
  mutate(
   sexo_recode = recode(
    sexo,
    "Fêmea" = "Fêmea",
    "Macho" = "Macho",
    "fêmea" = "Fêmea",
    "Não coletado" = "Não coletado"
   ) 
  ) %>% 
  group_by(sexo_recode) %>% 
  summarise(
    n = n())
```

    ## # A tibble: 3 x 2
    ##   sexo_recode      n
    ##   <chr>        <int>
    ## 1 Fêmea        28331
    ## 2 Macho        21469
    ## 3 Não coletado 49570

**a**</br> Pelo dado abaixo a diferença é de 24.22%

``` r
(28331 - 21469)
```

    ## [1] 6862

``` r
(6862/28331) * 100
```

    ## [1] 24.22082

**b**</br>Pelos dados calculados abaixo: O sexo de peixe que tem maior
peso é o da Fêmea.

``` r
dados_prm %>% 
  mutate(
   sexo_recode = recode(
    sexo,
    "Fêmea" = "Fêmea",
    "Macho" = "Macho",
    "fêmea" = "Fêmea",
    "Não coletado" = "Não coletado"
   ) 
  ) %>% 
  select(peso_g, sexo_recode) %>% 
  group_by(sexo_recode) %>% 
  drop_na() %>% 
  summarise(
    n = sum(peso_g))
```

    ## # A tibble: 3 x 2
    ##   sexo_recode         n
    ##   <chr>           <dbl>
    ## 1 Fêmea        7643750.
    ## 2 Macho        4498112.
    ## 3 Não coletado 8329769.

**Questão 4**</br>Pelos dados calculados abaixo: Os Machos são 8552.

``` r
dados_prm %>% 
  distinct(habito_alimentar)
```

    ## # A tibble: 5 x 1
    ##   habito_alimentar
    ##   <chr>           
    ## 1 Onívoro         
    ## 2 Carnívoro       
    ## 3 Detritívoro     
    ## 4 Herbívoro       
    ## 5 Indeterminado

``` r
dados_prm %>% 
  mutate(
   sexo_recode = recode(
    sexo,
    "Fêmea" = "Fêmea",
    "Macho" = "Macho",
    "fêmea" = "Fêmea",
    "Não coletado" = "Não coletado"
   ) 
  ) %>% 
  filter(habito_alimentar == "Carnívoro") %>% 
  group_by(sexo_recode) %>% 
  summarise(
    n = n())
```

    ## # A tibble: 3 x 2
    ##   sexo_recode      n
    ##   <chr>        <int>
    ## 1 Fêmea        13903
    ## 2 Macho         8552
    ## 3 Não coletado 11476

II Sobre o dataset “contracheque.csv”</br>

**Questão 5**</br>Pelos dados calculados abaixo:O maior redimento
líquido é 7267672.

``` r
dados_ctc <- read_csv("dados/brutos/contracheque.csv")
```

    ## 
    ## -- Column specification --------------------------------------------------------
    ## cols(
    ##   .default = col_double(),
    ##   cpf = col_logical(),
    ##   nome = col_character(),
    ##   cargo = col_character(),
    ##   lotacao = col_character(),
    ##   url = col_character(),
    ##   tribunal = col_character(),
    ##   orgao = col_character(),
    ##   data_de_publicacao = col_date(format = ""),
    ##   mesano_de_referencia = col_character()
    ## )
    ## i Use `spec()` for the full column specifications.

    ## Warning: 2629 parsing failures.
    ##   row                col   expected              actual                            file
    ## 20914 data_de_publicacao date like  2018-05-11T08:53:36 'dados/brutos/contracheque.csv'
    ## 20915 data_de_publicacao date like  2018-05-11T08:53:36 'dados/brutos/contracheque.csv'
    ## 20916 data_de_publicacao date like  2018-05-11T08:53:36 'dados/brutos/contracheque.csv'
    ## 20917 data_de_publicacao date like  2018-05-11T08:53:36 'dados/brutos/contracheque.csv'
    ## 20918 data_de_publicacao date like  2018-05-11T08:53:36 'dados/brutos/contracheque.csv'
    ## ..... .................. .......... ................... ...............................
    ## See problems(...) for more details.

``` r
dados_ctc %>% view() 
```

``` r
dados_ctc %>% 
  group_by(rendimento_liquido) %>% 
  summarise(n = n()) %>% 
    arrange(desc(rendimento_liquido))
```

    ## # A tibble: 90,937 x 2
    ##    rendimento_liquido     n
    ##                 <dbl> <int>
    ##  1           7267672.     1
    ##  2           2874516.     1
    ##  3            683094.     1
    ##  4            660934.     1
    ##  5            511424.     1
    ##  6            477756.     1
    ##  7            422214.     1
    ##  8            421106.     1
    ##  9            398141.     1
    ## 10            389054.     1
    ## # ... with 90,927 more rows

**Questão 6**</br>Pelos dados calculados abaixo:37334 magistrados
receberam acima do valor 39293.32.

``` r
dados_ctc %>% 
  distinct(cargo) %>% view()
```

``` r
dados_ctc %>% 
  filter(rendimento_liquido > 39293.32) %>% 
  count()
```

    ## # A tibble: 1 x 1
    ##       n
    ##   <int>
    ## 1 37334

**a**</br>Pelos dados calculados abaixo:1136 magistrados receberam acima
do valor 100000.

``` r
dados_ctc %>% 
  filter(rendimento_liquido > 100000) %>% 
  count()
```

    ## # A tibble: 1 x 1
    ##       n
    ##   <int>
    ## 1  1136

**b**</br>Pelos dados calculados abaixo: O Tribunal Regional do Trabalho
da 7ª Região (CE) é que possui maior variabilidade.

``` r
dados_ctc %>% 
  distinct(tribunal)
```

    ## # A tibble: 128 x 1
    ##    tribunal                                                                
    ##    <chr>                                                                   
    ##  1 Superior Tribunal de Justiça                                            
    ##  2 Superior Tribunal Militar                                               
    ##  3 Conselho Nacional de Justiça                                            
    ##  4 Tribunal Superior do Trabalho / Conselho Superior da Justiça do Trabalho
    ##  5 Tribunal Superior Eleitoral                                             
    ##  6 Conselho da Justiça Federal                                             
    ##  7 Tribunal Regional Federal da 1a Região                                  
    ##  8 Tribunal Regional Federal da 2a Região                                  
    ##  9 Tribunal Regional Federal da 3a Região                                  
    ## 10 Tribunal Regional Federal da 4a Região                                  
    ## # ... with 118 more rows

``` r
dados_ctc %>% 
  summarise(
    media_rendimento = mean(rendimento_liquido)
  )
```

    ## # A tibble: 1 x 1
    ##   media_rendimento
    ##              <dbl>
    ## 1               NA

``` r
dados_ctc %>% 
  group_by(tribunal) %>% 
  select(rendimento_liquido) %>% 
  drop_na() %>% 
  summarise(
    media_rendimento = mean(rendimento_liquido)
  )
```

    ## Adding missing grouping variables: `tribunal`

    ## # A tibble: 128 x 2
    ##    tribunal                            media_rendimento
    ##    <chr>                                          <dbl>
    ##  1 Conselho da Justiça Federal                    1328.
    ##  2 Conselho Nacional de Justiça                   6333.
    ##  3 Superior Tribunal de Justiça                  28823.
    ##  4 Superior Tribunal Militar                     30118.
    ##  5 Tribunal de Justiça da Bahia                  34935.
    ##  6 Tribunal de Justiça da Paraíba                26949.
    ##  7 Tribunal de Justiça de Alagoas                37809.
    ##  8 Tribunal de Justiça de Goiás                  30591.
    ##  9 Tribunal de Justiça de Minas Gerais           46560.
    ## 10 Tribunal de Justiça de Pernambuco             22337.
    ## # ... with 118 more rows

``` r
dados_ctc %>% 
  group_by(tribunal) %>% 
  select(rendimento_liquido) %>% 
  drop_na() %>% 
  summarise(
    dp_rendimento = sd(rendimento_liquido), dp_rendimento = n()) %>% 
  arrange(desc(dp_rendimento))
```

    ## Adding missing grouping variables: `tribunal`

    ## # A tibble: 128 x 2
    ##    tribunal                                 dp_rendimento
    ##    <chr>                                            <int>
    ##  1 Tribunal de Justiça de São Paulo                 17220
    ##  2 Tribunal de Justiça de Minas Gerais               9278
    ##  3 Tribunal de Justiça do Rio de Janeiro             7629
    ##  4 Tribunal de Justiça do Rio Grande do Sul          7347
    ##  5 Tribunal de Justiça do Paraná                     6362
    ##  6 Tribunal de Justiça de Goiás                      4270
    ##  7 Tribunal de Justiça de Pernambuco                 4174
    ##  8 Tribunal Regional Federal da 1a Região            4092
    ##  9 Tribunal de Justiça de Santa Catarina             3960
    ## 10 Tribunal de Justiça da Bahia                      3605
    ## # ... with 118 more rows

``` r
dados_ctc %>% 
  group_by(tribunal) %>% 
  select(rendimento_liquido) %>% 
  drop_na() %>% 
  summarise(
    cv = (sd(rendimento_liquido)/mean(rendimento_liquido)) * 100)  
```

    ## Adding missing grouping variables: `tribunal`

    ## # A tibble: 128 x 2
    ##    tribunal                               cv
    ##    <chr>                               <dbl>
    ##  1 Conselho da Justiça Federal          61.2
    ##  2 Conselho Nacional de Justiça        169. 
    ##  3 Superior Tribunal de Justiça         57.2
    ##  4 Superior Tribunal Militar            26.8
    ##  5 Tribunal de Justiça da Bahia         38.4
    ##  6 Tribunal de Justiça da Paraíba       12.7
    ##  7 Tribunal de Justiça de Alagoas       72.6
    ##  8 Tribunal de Justiça de Goiás         62.2
    ##  9 Tribunal de Justiça de Minas Gerais  39.5
    ## 10 Tribunal de Justiça de Pernambuco    33.0
    ## # ... with 118 more rows

``` r
dados_ctc %>% 
  group_by(tribunal) %>% 
  select(rendimento_liquido) %>% 
  drop_na() %>% 
  summarise(
    cv_rendimento = (sd(rendimento_liquido)/mean(rendimento_liquido)) * 100) %>% 
  arrange(desc(cv_rendimento)) %>% view()
```

    ## Adding missing grouping variables: `tribunal`

**Questão 7**

``` r
dados_cp <- read_csv("dados/brutos/cursos-prouni.csv")
```

    ## 
    ## -- Column specification --------------------------------------------------------
    ## cols(
    ##   .default = col_double(),
    ##   grau = col_character(),
    ##   turno = col_character(),
    ##   curso_busca = col_character(),
    ##   cidade_busca = col_character(),
    ##   uf_busca = col_character(),
    ##   cidade_filtro = col_character(),
    ##   universidade_nome = col_character(),
    ##   campus_nome = col_character(),
    ##   nome = col_character()
    ## )
    ## i Use `spec()` for the full column specifications.

``` r
dados_cp %>% view()
```

``` r
dados_cp %>% 
  select(nome)
```

    ## # A tibble: 41,447 x 1
    ##    nome      
    ##    <chr>     
    ##  1 Medicina  
    ##  2 Enfermagem
    ##  3 Medicina  
    ##  4 Psicologia
    ##  5 Medicina  
    ##  6 Medicina  
    ##  7 Medicina  
    ##  8 Medicina  
    ##  9 Medicina  
    ## 10 Medicina  
    ## # ... with 41,437 more rows

``` r
dados_cp %>% 
  distinct(nome)
```

    ## # A tibble: 296 x 1
    ##    nome                    
    ##    <chr>                   
    ##  1 Medicina                
    ##  2 Enfermagem              
    ##  3 Psicologia              
    ##  4 Engenharia de Computação
    ##  5 Educação Física         
    ##  6 Direito                 
    ##  7 Engenharia de Produção  
    ##  8 Fisioterapia            
    ##  9 Administração           
    ## 10 Engenharia Civil        
    ## # ... with 286 more rows

**a**</br>Atravez da observação do gráfico a resposta é integral

**b**</br> Pelos dados calculados abaixo: encontramos a média e mediana
do turno integral.

``` r
dados_cp %>% 
  group_by(turno) %>% 
  select(nota_integral_ampla) %>% 
  drop_na() %>% 
  summarise(
    media_nota = mean(nota_integral_ampla)
  )
```

    ## Adding missing grouping variables: `turno`

    ## # A tibble: 5 x 2
    ##   turno             media_nota
    ##   <chr>                  <dbl>
    ## 1 Curso a Distância       545.
    ## 2 Integral                663.
    ## 3 Matutino                609.
    ## 4 Noturno                 602.
    ## 5 Vespertino              622.

``` r
dados_cp %>% 
  group_by(turno) %>% 
  select(nota_integral_ampla) %>% 
  drop_na() %>% 
  summarise(
    mediana_nota = median(nota_integral_ampla)
  )
```

    ## Adding missing grouping variables: `turno`

    ## # A tibble: 5 x 2
    ##   turno             mediana_nota
    ##   <chr>                    <dbl>
    ## 1 Curso a Distância         552.
    ## 2 Integral                  658.
    ## 3 Matutino                  610.
    ## 4 Noturno                   602.
    ## 5 Vespertino                621.

**c**</br> Pelos dados calculados abaixo: Dentre os cinco turnos, o que
possui menor homegeneidade na nota integral ampla é Curso a Distância,
porque apresenta a maior porcentagem.

``` r
dados_cp %>% 
  group_by(turno) %>%
  select(nota_integral_ampla) %>% 
  drop_na() %>% 
  summarise(
    Desvio_p = sd(nota_integral_ampla))
```

    ## Adding missing grouping variables: `turno`

    ## # A tibble: 5 x 2
    ##   turno             Desvio_p
    ##   <chr>                <dbl>
    ## 1 Curso a Distância     53.2
    ## 2 Integral              58.0
    ## 3 Matutino              43.5
    ## 4 Noturno               41.2
    ## 5 Vespertino            41.0

``` r
dados_cp %>% 
  group_by(turno) %>%
  select(nota_integral_ampla) %>% 
  drop_na() %>% 
  summarise(
    cv = (sd(nota_integral_ampla)/mean(nota_integral_ampla) * 100))
```

    ## Adding missing grouping variables: `turno`

    ## # A tibble: 5 x 2
    ##   turno                cv
    ##   <chr>             <dbl>
    ## 1 Curso a Distância  9.77
    ## 2 Integral           8.75
    ## 3 Matutino           7.14
    ## 4 Noturno            6.85
    ## 5 Vespertino         6.59

**Questão 8**</br>Pelos dados calculados abaixo:O Estado da Bahia ocupa
a 5° posição em ordem decrescente.

``` r
dados_cp %>% 
  group_by(uf_busca) %>%
  summarise(
    n = n()
  )%>% 
  arrange(desc (n)) %>% view()
```

**Questão 9**</br>Pelo dado calculado abaixo: Foram identificado
distintamente 296 cursos na variável nome.

``` r
dados_cp %>% 
  distinct(nome) %>% view()
```

**Questão 10**</br> Observando os gráfico, consigo descreve que o
gráfico do curso de medicina tem uma destribuição simétrica, o que
indica que a média e a mediana converge.Quanto ao gráfico do curso de
direito, apresenta uma distribuição assimétrica o que indica que a média
tem desvantagem em relação a mediana, assim para este tipo de gráfico a
melhor tendência e o desvio padrão.
