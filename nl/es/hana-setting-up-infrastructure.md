---



copyright:
  years: 2017, 2018
lastupdated: "2010-03-05"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 2. Configuración de la infraestructura
{: #set_up_infrastructure}

En la siguiente sección se describe cómo configurar los {{site.data.keyword.baremetal_long}} de SAP HANA, red, seguridad, almacenamiento y sistema operativo. Póngase en contacto con el [Soporte de {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support) si tiene alguna pregunta.

## Realización del pedido de servidor
{: order-server}

Utilice los siguientes pasos para realizar el pedido de {{site.data.keyword.baremetal_short}}. Encontrará información adicional en [Configuración del servidor nativo](https://console.bluemix.net/docs/bare-metal/configuring.html#configuring-your-bare-metal-server) utilizando sus credenciales exclusivas.

1. Inicie sesión en el [portal del cliente de la infraestructura de {{site.data.keyword.cloud_notm}}](https://control.softlayer.com) con sus credenciales exclusivas.
2. Pulse el icono **Dispositivos** en la página Resumen de la cuenta.
3. Pulse el enlace **Mensual** en {{site.data.keyword.baremetal_short}} en la página Dispositivos. Se abre el recuadro de diálogo Lista de servidores.
4. Los servidores certificados por SAP están en la parte superior de la lista. Pulse el hiperenlace de **Precio inicial al mes** para seleccionar el servidor adecuado y pasar a la página de configuración y pedido. Los servidores certificados por SAP HANA se identifican con **-H** bajo el Modelo de CPU.  
5. Escriba el número de servidores del pedido que realiza en el campo **Calidad** y seleccione su **Centro de datos**.
6. Las opciones de **Servidor**, **RAM**, **Sistema operativo** y almacenamiento privado se establecen de forma predeterminada en función de la selección de servidor y no se pueden modificar. El dimensionamiento del almacenamiento se realiza en línea con los tamaños que necesita SAP HANA con una determinada cantidad de RAM. El pedido de {{site.data.keyword.blockstorageshort}} de {{site.data.keyword.IBM_notm}} para {{site.data.keyword.cloud_notm}} o {{site.data.keyword.filestorage_full_notm}} y el almacenamiento adjunto en red (NAS) se realiza después del pedido de servidor.
7. Seleccione el **Sistema operativo** de Red Hat o Microsoft y seleccione el sistema operativo específico o hipervisor VMware para su servidor.

## Selección de las opciones de servidor
{: #select_options}

En el siguiente paso, seleccionará el tipo y el número de discos que desea añadir a la configuración. También puede seleccionar distintas opciones para grupos de almacenamiento de RAID (matriz redundante de discos independientes) y diseños de particiones sobre grupos de almacenamiento de RAID. Para obtener más información, consulte [Acerca de RAID](https://console.bluemix.net/docs/bare-metal/what-raid.html#about-raid} or [{{site.data.keyword.cloud_notm}} Support](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support).

1. En **Servidores certificados de SAP**, realice la selección sobre la base de cómo tenga previsto utilizar el servidor. Encontrará detalles sobre cada opción en [Configuración de los servidores nativos](https://console.bluemix.net/docs/bare-metal/configuring.html#setting-up-your-bare-metal-servers). También puede consultar la herramienta [Design Decision Tool](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool) (desplácese hacia abajo) o el [Soporte de {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support) para obtener más información.
2. Pulse **Añadir a pedido** en la parte inferior de la página.

## Ajuste de las configuraciones avanzadas del sistema
{: #adv_config}

1. Siga las directrices de [Configuración avanzada del sistema](https://console.bluemix.net/docs/bare-metal/configuring.html#advanced-system-configuration) para obtener ayuda con los valores de la ventana **Configuración avanzada del sistema**.

Los nombres de host de SAP deben constar de un máximo de 13 caracteres alfanuméricos. Para obtener más información sobre el nombre de host SAP, consulte las [Notas de SAP 611361](https://launchpad.support.sap.com/#/611361) y [129997](https://launchpad.support.sap.com/#/129997). 

## Confirmación de las selecciones
{: #confirm_selections}

1. Confirme las selecciones en la página de pago y marque **Términos de los servicios en la nube** y **Acuerdo de software de terceros**.
2. Desplácese a Crear cuenta: Datos de facturación y especifique el **Tipo de pago, Nombre, Tarjeta** y **Vencimiento** (fecha) de la tarjeta de crédito que se utilizará para la facturación.
3. Pulse **Enviar pedido**. Se le redirigirá a una página con el número de pedido. Puede imprimir la página, ya que también es su recibo del pedido.

Se le enviará un correo electrónico de confirmación con el asunto _Se ha aprobado el pedido número ## de {{site.data.keyword.cloud_notm}}_ a la dirección de correo electrónico de su perfil. Este correo electrónico es un aviso de que el servidor ha sido aprobado y está en proceso de ser desplegado. Una vez desplegado, se envía otro aviso notificando que el servidor está disponible y puede gestionarse a través del [portal del cliente de infraestructura de {{site.data.keyword.cloud_notm}}](https://control.softlayer.com).

## Siguientes pasos

Ahora está listo para empezar a gestionar los {{site.data.keyword.baremetal_short}}. Consulte [Gestión del entorno SAP HANA](/docs/infrastructure/sap-hana/hana-manage-environment.html).
