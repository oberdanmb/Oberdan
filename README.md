
<!DOCTYPE html>
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
  <meta name="description" content="Operação On-Line">
  <meta name="author" content="Itamar Soares">
  <meta name="keyword" content="">
  <link rel="shortcut icon" href="img/favicon.png">
  <meta http-equiv="expires" content="Mon, 26 Jul 1997 05:00:00 GMT" />
  <meta http-equiv="pragma" content="no-cache" />
  <meta http-equiv="cache-control" content="max-age=0" />
  <meta http-equiv="cache-control" content="no-cache" />
  <meta http-equiv="expires" content="0" />

  <title>Plataforma Digital</title>

  <!-- Custom Css -->
  <link href="css/style.css" rel="stylesheet">
  <link href="css/jquery.dataTables.min.css" rel="stylesheet">
  <link href="css/estilofixo.css" rel="stylesheet">
  <link href="css/payment.css" rel="stylesheet">
  <link href="css/jquery-te-1.4.0.css" rel="stylesheet">
  <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.7.2/css/all.css" integrity="sha384-fnmOCqbTlWIlj8LyTjo7mOUStjsKC4pOpQbqyi7RrhN7udi9RwhKkMHpvLbHG9Sr" crossorigin="anonymous">
  <link href="https://fonts.googleapis.com/css?family=Montserrat:400,500,600,700,800,900" rel="stylesheet">
  <link href="js/libs/animate.min.css" rel="stylesheet">
  <link href="js/libs/angular-toastr.css" rel="stylesheet">
  <link href="js/libs/ng-tags-input.css" rel="stylesheet">
  <link href="js/libs/angular-block-ui.css" rel="stylesheet" />
  <link href="https://cdn.datatables.net/1.10.19/css/jquery.dataTables.min.css" rel="stylesheet">
  <link href="https://cdn.datatables.net/buttons/1.5.2/css/buttons.dataTables.min.css" rel="stylesheet">
  <link href="https://cdn.datatables.net/responsive/2.2.3/css/responsive.dataTables.min.css" rel="stylesheet">
</head>

<body id="bodyplataform" ng-controller='indexCtrl' class="app header-fixed sidebar-fixed sidebar-hidden aside-menu-fixed aside-menu-hidden">

  <div id="blockoperador" class="blockuserinterface" ng-controller="discadorCtrl">
    <h1 id="msgblock"></h1>
    <div class="card p-4 w-50 m-auto card-bloqueio">
      <div class="card-block ">
        <form ng-submit="desbloquearusuario2()">
          <p id="msgerro"></p>
          <div id="contagempausa" class="row">
            <div class="col text-center">
              <p id="contadorstatus">Você está em <b>{{statusdiscadoroperador[0].statusOperador}}</b> à <b>{{statusdiscadoroperador[0].Tempo}}</b></p>
            </div>
          </div>
          <div class="input-group mb-4">
            <span class="input-group-addon"><i class="fas fa-lock"></i></span>
            <input type="password" class="form-control" ng-model="bloqueio.senha" placeholder="Senha" required>
          </div>
          <div class="row">
            <div id="btnunlock" class="col text-center">
              <button id="btnunlockitself" type="submit" class="btn btn-primary px-4">Desbloquear</button>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>

  <div id="pausasuporte" class="blocksuporte">
    <h2>Atenção.</h2> <br>
    <h4>Estamos realizando alguns ajustes na plataforma e em seu navegador, por favor aguarde.</h4>
    <h3><i class="fas fa-medkit"></i></h3>
  </div>

  <div id="required-field" class="sidebutton" permission permission-only="['canAll']">
    <div class="sidebuttoncontent">
      <label class="switch switch-sm switch-text switch-required">
        <input id="requiredcheck" class="switch-input" type="checkbox" ng-click="togglerequired(this)" checked>
        <span class="switch-label" data-on="✔" data-off="✖"></span>
        <span class="switch-handle"></span>
      </label>
    </div>
    <div class="sidebuttontoggle">
      <i class="fas fa-eye"></i>
    </div>
  </div>

  <div id="favorite-shortcut" class="sidebutton"  permission permission-only="['canAll']">
    <div class="sidebuttoncontent">
      <div class="card-shortcut mx-3" ng-repeat="item in favoriteshortcuts | orderBy: 'count' | limitTo: 3">
        <a href="{{item.url}}" target="_blank">
          <div class="sidebutton-container-shortcut">
            <i class="{{item.icon}} animated pulse infinite"></i>
          </div>
        </a>
      </div>
    </div>
    <div class="sidebuttontoggle">
      <i class="fas fa-cut"></i>
    </div>
  </div>

  <!-- User Interface -->
  <ui-view></ui-view>

  <!-- Bootstrap and necessary plugins -->

  <script src="js/libs/moment.min.js"></script>
  <script type="text/javascript" src="js/jquery-3.4.0.slim.min.js"></script>
  <!-- <script src="https://code.jquery.com/jquery-3.2.1.slim.min.js" integrity="sha384-KJ3o2DKtIkvYIK3UENzmM7KCkRr/rE9/Qpg6aAZGJwFDMVNA/GpGFF93hXpG5KkN" crossorigin="anonymous"></script> -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.12.9/umd/popper.min.js" integrity="sha384-ApNbgh9B+Y1QKtv3Rn7W3mgPxhU9K/ScQsAP7hUibX39j7fakFPskvXusvfa0b4Q" crossorigin="anonymous"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/js/bootstrap.min.js" integrity="sha384-JZR6Spejh4U02d8jOt6vLEHfe/JQGiRRSQQxSfFWpi1MquVdAyjUar5+76PVCmYl" crossorigin="anonymous"></script>


  <!-- AngularJS -->
  <script src="js/libs/angular.min.js"></script>
  <script src="js/libs/angular-cookies.min.js"></script>
  <script src="//ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular-sanitize.js"></script>



  <!-- AngularJS CoreUI App scripts -->
  <script src="js/app.js"></script>
  <script src="js/routes.js"></script>
  <script src="js/directives.js"></script>
  <script src="js/factory.js"></script>
  <script src="js/config.js"></script>
  <script src="js/JqueryMask.js"></script>

  <!-- AngularJS plugins -->
  <script src="js/libs/angular-ui-router.min.js"></script>
  <script src="js/libs/angular-storage.min.js"></script>
  <script src="js/libs/angular-permission.js"></script>
  <script src="js/libs/angular-permission-ui.js"></script>
  <script src="js/libs/angular-toastr.tpls.js"></script>
  <script src="js/libs/angular-viacep.min.js"></script>
  <script src="js/libs/angular-block-ui.min.js"></script>
  <script src="js/libs/query-builder-directive.js"></script>
  <script src="js/libs/ng-tags-input.js"></script>

  <script type="text/javascript" src="js/Plug-in/dataTable/jquery.dataTables.min.js"></script>
  <script src="https://cdn.datatables.net/1.10.19/js/jquery.dataTables.min.js"></script>
  <script src="https://cdn.datatables.net/buttons/1.5.2/js/dataTables.buttons.min.js"></script>
  <script src="https://cdn.datatables.net/buttons/1.5.2/js/buttons.flash.min.js"></script>
   <script src="https://cdn.datatables.net/buttons/1.5.2/js/buttons.html5.min.js"></script>
  <script src="https://cdn.datatables.net/buttons/1.5.2/js/buttons.print.min.js"></script>

  <script src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.53/vfs_fonts.js"></script>
  <script src="https://cdn.datatables.net/buttons/1.5.6/js/buttons.html5.min.js"></script>
  <script src="https://cdn.datatables.net/buttons/1.5.6/js/buttons.print.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.36/vfs_fonts.js"></script>

  <script src="//cdnjs.cloudflare.com/ajax/libs/angular-filter/0.4.7/angular-filter.js"></script>
  <script src="js/libs/Chart.min.js"></script>
  <script src="js/libs/angular-chart.min.js"></script>


  <!-- Externo plugins -->
  <script src="js/libs/rltm.js"></script>
  <script src="js/libs/angular-chat.js"></script>
  <script src="js/libs/angular-input-masks-standalone.min.js"></script>



  <!-- Controllers -->
  <script src="js/controller/shared.js"></script>
  <script src="js/controller/css.js"></script>
  <script src="js/controller/acionamento/acionamento.js"></script>
  <script src="js/controller/acionamento/produtos.js"></script>
  <script src="js/controller/acionamento/creditcardCtrl.js"></script>
  <script src="js/controller/acionamento/tabulacao.js"></script>
  <script src="js/controller/inteligencia/monitoroperador.js"></script>
  <script src="js/controller/inteligencia/carga.js"></script>
  <script src="js/controller/inteligencia/raiox.js"></script>
  <script src="js/controller/inteligencia/ligacoes.js"></script>
  <script src="js/controller/inteligencia/eficienciauf.js"></script>
  <script src="js/controller/dashboards/dashboard.js"></script>
  <script src="js/controller/formularios/psa.js"></script>
  <script src="js/controller/administracao/user.js"></script>
  <script src="js/controller/administracao/cadastroparceiros.js"></script>
  <script src="js/controller/administracao/cadastroconfiguracoes.js"></script>
  <script src="js/controller/administracao/acompanhamento.js"></script>
  <script src="js/controller/administracao/acompanhamento.js"></script>
  <script src="js/controller/administracao/cadastrooperacao.js"></script>
  <script src="js/controller/administracao/cadastrosdiversos.js"></script>
  <script src="js/controller/seguros/seguros.js"></script>
  <script src="js/controller/ti/ti.js"></script>

  <!-- Discador Callflex -->
  <script src="js/discador/callflex_engine.js"></script>


  <!-- Modulos CredGroup -->
  <script src="js/modulos/login/loginAPP.js"></script>
  <script src="js/modulos/login/configloginAPP.js"></script>
  <script src="js/modulos/chat/chatAPP.js"></script>
  <script src="js/modulos/chat/configchatAPP.js"></script>

  <!-- jQuery -->

  <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js" integrity="sha384-ZMP7rVo3mIykV+2+9J3UJ46jBk0WLaUAdn689aCwoqbBJiSnjAK/l8WvCWPIPm49" crossorigin="anonymous"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.13.4/xlsx.core.min.js"></script>

  <script type="text/javascript" src="js/Plug-in/ZeroClipboard/ZeroClipboard.js"></script>
  <script type="text/javascript" src="js/Plug-in/TableExport/jquery.tableexport.v2.js"></script>
  <script type="text/javascript" src="js/Plug-in/jqte/jquery-te-1.4.0.min.js"></script>
  <script type="text/javascript" src="js/Plug-in/jqueryMask.js"></script>
  <script type="text/javascript" src="js/Plug-in/simpleUpload.php"></script>

  <script type="text/javascript">
    $(document).ready(function() {
      $("#requiredid").click();
    });
  </script>


</body>

</html>
