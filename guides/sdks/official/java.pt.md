# MercadoPago SDK para Java

Esta biblioteca fornece um conjunto de classes e métodos para interagir com a API do Mercado Pago.

### Versões do Java suportadas:

Nosso SDK é compatível com Java versão 8 ou maior.

## Instalação

### Usando Maven

1) Anexe dependências do MercadoPago para pom.xml

  ```xml
    ...
    <dependencies>
        <dependency>
            <groupId> com.mercadopago </groupId>
            <artifactId> dx-java </artifactId>
            <version> 1.2.1 </version>
        </dependency>
    </dependencies>
    ...
  ```
  
2) Execute `mvn install`, isso é tudo, você tem o SDK do Mercadopago instalado.

## Começo rápido

1) Importar as classes básicas de Mercado Pago. `import import com.mercadopago.*;`

2) Configure suas credenciais.

    ```java
      MercadoPago.SDK.setAccessToken("ACCESS_TOKEN");
    ```

> Encontre toda a informação sobre suas credenciais em nossas [perguntas frequentes](https://www.mercadopago.com.br/developers/pt/guides/resources/faqs/credentials/).

3) Usando objetos de recursos.

![SDK resource structure of Mercado Pago](https://user-images.githubusercontent.com/864790/34393059-9acad058-eb2e-11e7-9987-494eaf19d109.png)

**Examplo**

```java
  import com.mercadopago.*;
  import com.mercadopago.exceptions.MPConfException;
  import com.mercadopago.exceptions.MPException;
  import com.mercadopago.resources.Payment;
  import com.mercadopago.resources.datastructures.payment.Payer;

  public class Main {

      public static void main(String[] args)throws MPException, MPConfException {

          MercadoPago.SDK.setClientSecret(System.getenv("CLIENT_SECRET_OK"));
          MercadoPago.SDK.setClientId(System.getenv("CLIENT_ID_OK"));

          Payment payment = new Payment()
                  .setTransactionAmount(100f)
                  .setToken("your_cardtoken")
                  .setDescription("description")
                  .setInstallments(1)
                  .setPaymentMethodId("visa")
                  .setPayer(new Payer()
                          .setEmail("dummy_email"));

          payment.save();

          System.out.println(payment.getStatus());

      }
  }
```
