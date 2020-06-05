# GxSweetAlert
User Control Object - Sweet Alert (GeneXus)

<p align="center">
  <a href="https://sweetalert2.github.io/">
    <img src="https://github.com/GxBrasilNOficial/GxSweetAlert/blob/master/GxSweetAlert/SwertAlertDemo.gif?raw=true" width="562"><br>
    See SweetAlert2 in action ↗
  </a>
</p>

## Instalação

Genexus 16 ou Superior:

```sh
1 - Na IDE Genexus, navegue em Knowledge Manager / Import.
2 - Selecione o Arquivo ucGxSweetAlert.xml ** Note que é preciso alterar o filtro da caixa de seleção para XML.
```

## Exemplo de uso
```Gx
Event Start
	&Titulo = Form.Caption
	&Mensagem = "Conhece o Mário?"
	&Timer     = 2000 //em Milisegundos
	ucSweetAlert1.ConvertGxMessages = true //Habilita para Converter Mensagem do gx
Endevent

Event 'Fire'
	ucSweetAlert1.Fire(&Titulo, &Mensagem, &SweetIcon,"Confirmar","green")
Endevent

Event &SweetPosition.ControlValueChanged
	ucSweetAlert1.Position = &SweetPosition	
	ucSweetAlert1.Fire(&Titulo, &Mensagem, &SweetIcon,"To aqui","green")
EndEvent

Event 'Toast'
	ucSweetAlert1.EventName = 'Toast'
	ucSweetAlert1.FireToast(&Titulo, "Tem esse Toast", &SweetIcon,&Timer )
	
Endevent

Event ucSweetAlert1.ClosedTimer
	
	//Evento disparado quando o Toast é fechado
	if ucSweetAlert1.EventName = 'Toast'
		ucSweetAlert1.EventName = ''
		ucSweetAlert1.FireToast2(&Titulo, "Tem esse Também", &SweetIcon,&Timer )	
	endif
	
EndEvent

Event 'Confirm'
	//Exemplo de Confirm
	ucSweetAlert1.EventName = 'MeuEvento'
	ucSweetAlert1.Confirm(&Titulo, &Mensagem, &SweetIcon, "Confirmar")
Endevent

Event ucSweetAlert1.Confirmed

	//Quando o usuário Confirma
	if ucSweetAlert1.EventName = 'MeuEvento'
		ucSweetAlert1.FireToast2(&Titulo, "Confirmou", SwalIcon.success,&Timer )
	endif

EndEvent


Event ucSweetAlert1.Cancel

	//Quando o usuário Cancela no Confirm
	if ucSweetAlert1.EventName = 'MeuEvento'
		ucSweetAlert1.FireToast2(&Titulo, "Desistiu", SwalIcon.error,&Timer )
	endif

EndEvent

Event 'Msg do Gx'
	Msg("Testando Toast")
Endevent
```
