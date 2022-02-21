# Troubleshooting

**Se nenhuma notificação for recebida**, será necessário aplicar a busca de pedidos como um método de contingência usando sua `external_reference`  como critério de busca. A busca pode ser feita de duas maneiras:

|Mecanismo|Descrição|
|---|---|
|Manual|O ponto de venda deve incluir um botão para realizar a pesquisa.|
|Automático|Após 30 segundos sem receber nenhuma notificação, uma busca de pedido é iniciada a cada intervalo de, por exemplo, 5 segundos.|

Para qualquer um dos mecanismos descritos acima, usaremos o seguinte endpoint:

```curl
curl --location --request GET 'https://api.mercadopago.com/merchant_orders?external_reference=EXTERNAL_REFERENCE' \
--header 'Authorization: Bearer ACCESS_TOKEN'
```

> NOTE
>
> Nota
>
> Esta solução usa a mesma [API](https://www.mercadopago[FAKER][URL][DOMAIN]/developers/pt/reference/merchant_orders/_merchant_orders_id/get) que usamos na seção [Consulta da ordem](https://www.mercadopago[FAKER][URL][DOMAIN]/developers/pt/guides/notifications/ipn/query-through-mo), adicionando o parâmetro de consulta `external_reference` para consultar o pagamento no caso de não receber a notificação.

A resposta será a mesma que usar o id de pagamento e devem usar os mesmos critérios mencionados acima para confirmar o pedido.

Se o QR em que o pedido foi publicado não tiver sido verificado, a resposta será:

```json
{
  "elements": null,
  "next_offset": 0,
  "total": 0
}
```

> WARNING
>
> Importante
>
> No Mercado Pago exigimos a padronização da integração dos pagamentos presenciais, que têm como principal método a notificação (IPN).
> <br>
> A busca de pedidos por `external_reference` deve ser utilizada apenas como contingência, caso nenhuma notificação seja recebida.

> PREV_STEP_CARD_PT
>
> Consulta da ordem
> 
> Verifique o status das ordens.
>
> [Consulta da ordem](https://www.mercadopago[FAKER][URL][DOMAIN]/developers/pt/guides/notifications/ipn/inperson-order-query)

> NEXT_STEP_CARD_PT
>
> Ferramentas adicionais
>
> Conheça sobre ferramentas adicionais para pesquisa de pagamento.
>
> [Ferramentas adicionais](https://www.mercadopago[FAKER][URL][DOMAIN]/developers/pt/guides/notifications/ipn/additional-tools)