# GxSweetAlert
User Control Object - Sweet Alert (GeneXus)

<p align="center">
  <a href="https://sweetalert2.github.io/">
    <img src="https://n00nqq.dm.files.1drv.com/y4pJlIr7SNXK4hQZK9RRDAnF0jkoJy0NuBtlJ_vmKId7rdcVdGQUoqhgKh3pshLai3HMMM9CqKQtaAMWNcNTsxUsl9ml8qTTQhOgdkyQQRAGFGWLXjM5jl1wW5Yi-8G7GaP2l2Ks_B-g2AZj049lqcoKly9yWmXnYhFmuGTk9AOclPS2wY32SX9RSe0LojTB8-fq-nTU4X73osA-Yesp5jsbA/SwertAlertDemo.gif?psid=1" width="562"><br>
    See SweetAlert2 in action ↗
  </a>
</p>

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
