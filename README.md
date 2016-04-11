# helloword

<body>
  <div id="main">
    <h2>Seus botões</h2>
    <div id="botoes"></div>
    <br />
    <button id="adicionar">Adicionar Botão</button>
    <br />
  </div>
  <div id="config">
    <h2>Configurar o botão</h2>
    <p>Selecione a cor</p>
    <div class="cor" id="azul"></div>
    <div class="cor" id="cinza"></div>
    <div class="cor" id="laranja"></div>
    <div class="cor" id="preto"></div>
    <div class="cor" id="roxo"></div>
    <div class="cor" id="verde"></div>
    <br />
    <p>
      Tamanho do botão:
      <select id="tamanho">
        <option value="209x48">Grande</option>
        <option value="164x37">Médio</option>
        <option value="94x52">Pequeno</option>
      </select>
    </p>
    <br />
    <button id="excluir">Excluir Botão</button>
    <br />
    <button id="cancelar">Cancelar Edição</button>
  </div>
</body>


$('#adicionar').click(function() {
  $('#botoes').append('<img class="botao" src="https://p.simg.uol.com.br/out/pagseguro/i/botoes/doacoes/209x48-doar-assina.gif" />');
});
$('#botoes').on('click', '.botao', function() {
  $('.botao.selected').removeClass('selected')
  $(this).addClass('selected');
  $('#config').show();
});
$('#cancelar').click(function() {
  $('#config').hide();
  $('.selected').removeClass('selected')
});
$('#excluir').click(function() {
  $('#config').hide();
  $('.botao.selected').remove();
});
$('.cor').click(function() {
  $('.cor.selected').removeClass('selected')
  $(this).addClass('selected');
  $('.botao.selected').configurar($(this).attr('id'), $('#tamanho').val());
});
$('#tamanho').change(function() {
  $('.botao.selected').configurar($('.cor.selected').attr('id'), $('#tamanho').val());
});

(function($) {
  $.fn.configurar = function($cor, $tamanho) {
    if ($cor == "verde")
      $cor = "";
    else
      $cor = $cor + "-";
    return $(this).attr('src', "https://p.simg.uol.com.br/out/pagseguro/i/botoes/doacoes/" + $tamanho + "-doar-" + $cor + "assina.gif");
  };
})(jQuery);




#main {
  float: left;
  min-width: 250px;
  border: 1px solid Gray;
  padding: 10px;
}

#config {
  display: none;
  float: left;
  min-width: 250px;
  border: 1px solid Gray;
  padding: 10px;
}

.cor {
  width: 20px;
  height: 20px;
  float: left;
  margin: 0px 10px;
}

#azul {
  background-color: Blue;
}

#cinza {
  background-color: Gray;
}

#laranja {
  background-color: Orange;
}

#preto {
  background-color: Black;
}

#roxo {
  background-color: Purple;
}

#verde {
  background-color: Green;
}

#tamanho {
  clear: both;
}

.selected {
  border: 3px solid Red;
}

.botao {
  display: block;
  margin: 5px;
}
