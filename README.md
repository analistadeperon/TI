# TI
Autor: Matheus Deperon
https://github.com/analistadeperon
# Validador de contas bancárias

Projeto em construção. Por enquanto, siga as instruções a partir do projeto moip-sdk-js https://github.com/moip/moip-sdk-js#validação-de-conta-bancária
A validação da conta bancária é realizada sobre as regras dos seguintes bancos: Itaú, Bradesco, Banco do Brasil, Santander, Citibank e HSBC. Para os outros bancos é realizada uma validação padrão:
 * Agência de 1 até 5 números
 * Dígito da agência de 0 a 2 caracteres
 * Conta corrente de 1 até 12 números
 * Dígito da conta corrente de 0 a 2 caracteres

O número da agência e conta corrente dos bancos Itaú, Bradesco, e Banco do Brasil são validados através do cálculo do dígito verificador (semelhante a validação do CPF).

### Validador de conta bancária on-line
Você pode realizar a validação a qualquer momento através do site:
http://validadorbanco.com.br

# Implementação a validação em seu site

Para um funcionamento inicial, copie o trecho de código abaixo para sua página HTML. 


```html
<script type="text/javascript" src="http://code.jquery.com/jquery-2.1.3.min.js"></script>
<script type="text/javascript" src="https://cdn.rawgit.com/moip/bank-account-validator-js/master/dist/bank-account-validator.min.js"></script>
<script type="text/javascript">
  $(document).ready(function() {
    $("#validate_bank_account").click(function() {
      Moip.BankAccount.validate({
        bankNumber         : $("#bank_number").val(),
        agencyNumber       : $("#agency_number").val(),
        agencyCheckNumber  : $("#agency_check_number").val(),
        accountNumber      : $("#account_number").val(),
        accountCheckNumber : $("#account_check_number").val(),
        valid: function() {
          alert("Conta bancária válida")
        },
        invalid: function(data) {
          var errors = "Conta bancária inválida: \n";
          for(i in data.errors){
            errors += data.errors[i].description + "-" + data.errors[i].code + ")\n";
          }
          alert(errors);
        }
      });
    });
  });
</script>
<form>
  <select id="bank_number">
    <option value="001">BANCO DO BRASIL S.A.</option>
    <option value="237">BANCO BRADESCO S.A.</option>
    <option value="341">BANCO ITAÚ S.A.</option>
    <option value="104">CAIXA ECONOMICA FEDERAL</option>
    <option value="033">BANCO SANTANDER BANESPA S.A.</option>
    <option value="399">HSBC BANK BRASIL S.A.</option>
    <option value="151">BANCO NOSSA CAIXA S.A.</option>
    <option value="745">BANCO CITIBANK S.A.</option>
  </select>

  <input id="agency_number" placeholder="Agência" type="text"/>
  <input id="agency_check_number" placeholder="Dígito da agência" type="text" />
  <input id="account_number" placeholder="Conta corrente" type="text" />
  <input id="account_check_number" placeholder="Dígito da conta corrente" type="text" />

  <input type="button" value="Validar" id="validate_bank_account" />
</form>
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.0.1/jquery.min.js"></script>
<form id="formulario-1" action="" method="post" data-toggle="validator" role="form">
<table id="table_com_parcelas" class="table table-condensed table-hover table-responsive table-striped">
  <thead>
    <tr>
      <th class="align">Parcela</th>
      <th class="align">Vencimento</th>
      <th class="align">Valor</th>
      <th class="align">Forma pagamento</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="align">1 de 4</td>
      <td class="align">28/10/2017</td>
      <td class="align">R$ 2.750,00</td>
      <td class="align form">
        <div class="form-inline">
          <select class="form-control" id="select-1" required="true"><option value="">Selecione</option><option value="1">Boleto</option><option value="2">Cartão</option><option value="3">Cheque</option><option value="4">Dinheiro</option><option value="5">Transferência</option></select>
            <span class="form-full-1"></span>
        </div>
      </td>
    </tr>
    <tr>
      <td class="align">2 de 4</td>
      <td class="align">28/11/2017</td>
      <td class="align">R$ 2.750,00</td>
      <td class="align form">
        <div class="form-inline">
          <select class="form-control" id="select-2" required="true"><option value="">Selecione</option><option value="1">Boleto</option><option value="2">Cartão</option><option value="3">Cheque</option><option value="4">Dinheiro</option><option value="5">Transferência</option></select>
            <span class="form-full-2"></span>
        </div>
      </td>
    </tr>
    <tr>
      <td class="align">3 de 4</td>
      <td class="align">28/12/2017</td>
      <td class="align">R$ 2.750,00</td>
      <td class="align form">
        <div class="form-inline">
          <select class="form-control" id="select-3" required="true"><option value="">Selecione</option><option value="1">Boleto</option><option value="2">Cartão</option><option value="3">Cheque</option><option value="4">Dinheiro</option><option value="5">Transferência</option></select>
            <span class="form-full-3"></span>
        </div>
      </td>
    </tr>
    <tr>
      <td class="align">4 de 4</td>
      <td class="align">28/01/2018</td>
      <td class="align">R$ 2.750,00</td>
      <td class="align form">
        <div class="form-inline">
          <select class="form-control" id="select-4" required="true"><option value="">Selecione</option><option value="1">Boleto</option><option value="2">Cartão</option><option value="3">Cheque</option><option value="4">Dinheiro</option><option value="5">Transferência</option></select>
            <span class="form-full-4"></span>
        </div>
      </td>
    </tr>
  </tbody>
</table>
<button id="btn_checkout" name="btn_checkout" class="btn btn-warning pull-right">Salvar <span class="fa fa-angle-double-right"></span></button>

</form>
<!-- DADOS PESSOAIS-->
<fieldset>
 <legend>Dados Pessoais</legend>
 <table cellspacing="10">
  <tr>
   <td>
    <label for="nome">Nome: </label>
   </td>
   <td align="left">
    <input type="text" name="email">
   </td>
   <td>
    <label for="sobrenome">Sobrenome: </label>
   </td>
   <td align="left">
    <input type="text" name="sobrenome">
   </td>
  </tr>
  <tr>
   <td>
    <label>Nascimento: </label>
   </td>
   <td align="left">
    <input type="text" name="dia" size="2" maxlength="2" value="dd"> 
   <input type="text" name="mes" size="2" maxlength="2" value="mm"> 
   <input type="text" name="ano" size="4" maxlength="4" value="aaaa">
   </td>
  </tr>
  <tr>
   <td>
    <label for="rg">RG: </label>
   </td>
   <td align="left">
    <input type="text" name="rg" size="13" maxlength="13"> 
   </td>
  </tr>
  <tr>
   <td>
    <label>CPF:</label>
   </td>
   <td align="left">
    <input type="text" name="cpf" size="9" maxlength="9"> - <input type="text" name="cpf2" size="2" maxlength="2">
   </td>
  </tr>
 </table>
</fieldset>

<br />
<!-- ENDEREÇO -->
<fieldset>
 <legend>Dados de Endereço</legend>
 <table cellspacing="10">

  <tr>
   <td>
    <label for="rua">Rua:</label>
   </td>
   <td align="left">
    <input type="text" name="rua">
   </td>
   <td>
    <label for="numero">Numero:</label>
   </td>
   <td align="left">
    <input type="text" name="numero" size="4">
   </td>
  </tr>
  <tr>
   <td>
    <label for="bairro">Bairro: </label>
   </td>
   <td align="left">
    <input type="text" name="bairro">
   </td>
  </tr>
  <tr>
   <td>
