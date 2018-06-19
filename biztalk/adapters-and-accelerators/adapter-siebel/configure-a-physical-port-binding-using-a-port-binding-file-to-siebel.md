---
title: 設定實體連接埠繫結使用連接埠繫結檔案至 Siebel |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- port binding file
- physical port binding, configuring by using a port binding file
ms.assetid: 1758e89c-d56c-4e67-919b-c0bbb22878bf
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05bfa8539c223078fd29c5d99cfac50217bbaa36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222606"
---
# <a name="configure-a-physical-port-binding-using-a-port-binding-file-to-siebel"></a>設定使用連接埠繫結檔案至 Siebel 實體連接埠繫結
當您使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生 Siebel 成品，以外的結構描述檔案，中繼資料[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會產生連接埠繫結檔案。 您可以將此繫結檔案匯 BizTalk 應用程式建立實體傳送埠。 請參閱[重複使用 Siebel 配接器中的配接器繫結](../../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md)。 如果您匯入此繫結檔案，您不必手動建立實體傳送埠。  
  
> [!IMPORTANT]
>  同時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，如果您未指定類型字串的繫結屬性的值，且其預設值為 null 然後繫結屬性將不會使用繫結檔案中。 您必須以手動方式繫結屬性和其值在繫結檔案中，視需要新增。  
  
 建立永遠使用連接埠繫結檔案的連接埠建立雙向傳送埠。 如果您想要建立單向連接埠，您可以建立它以手動方式所遵循的步驟[設定實體連接埠繫結使用連接埠繫結檔案至 Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md)。 或者，您可以遵循本主題，以修改要建立單向連接埠的連接埠繫結檔案所述的因應措施。  
  
> [!IMPORTANT]
>  使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]並不會建立使用您可以建立 Wcf-siebel 連接埠的連接埠繫結檔案。 不過，您無法進行一些變更，所產生的連接埠繫結檔案至[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]並用它來建立 WCF Siebel 的連接埠。 如需詳細資訊，請參閱設定 Wcf-siebel 連接埠使用連接埠繫結檔案產生使用取用配接器服務增益集。  
  
 以下是一些您必須了解相對於所產生的繫結檔案的關鍵點[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]:  
  
-   使用特定的命名慣例，會建立檔案。 如果產生的中繼資料輸出的作業，將訊息傳送至 Siebel 系統，則檔案的名稱是 WcfSendPort_SiebelBinding_Custom.bindinginfo.xml。  
  
-   檔案包含的繫結組態、 繫結型別、 端點的 URI 和產生的中繼資料的作業為基礎的連接埠動作相關資訊。 當您匯入此繫結檔案，以建立連接埠時，才能設定實體連接埠的相關資訊會自動設定的連接埠上。  
  
    > [!IMPORTANT]
    >  根據預設，傳送埠上的動作會為您產生中繼資料的作業名稱對應。 例如，如果您產生帳戶商務元件上的插入作業的中繼資料，通訊埠上的動作設定為`<Operation Name="Insert" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert " />`。 不過，您在 BizTalk 協調流程中建立邏輯傳送連接埠上的作業名稱可能不能相同。 您必須確定邏輯連接埠 （在 BizTalk 協調流程中） 與實體傳送埠 （在 BizTalk Server 管理主控台） 中的作業名稱都相同。 如果沒有，您會收到錯誤時將訊息傳送至傳送埠透過 Siebel 系統。  
  
-   您只需要提供認證來連接至 Siebel 系統的連接埠。 繫結檔案並保留用來連接的使用者名稱，同時基於安全性的繫結檔案不包含密碼。  
  
## <a name="key-considerations-for-using-the-port-binding-file"></a>使用連接埠繫結檔案的重要考量  
  
-   當您匯入繫結檔案時，您可能會看到對話方塊通知訊息的繫結檔案中的 BizTalk 應用程式名稱不符合您要匯入繫結檔案的應用程式名稱。 您可以安全地忽略此訊息，並繼續。  
  
-   繫結檔案也包含名稱的連接埠和接收位置。 如果您要匯入繫結檔案的 BizTalk 應用程式建立連接埠或接收位置具有相同名稱做為相同的 BizTalk 應用程式中現有的連接埠，您會收到錯誤。 您必須手動編輯繫結檔案來指定唯一的名稱，連接埠或接收位置。  
  
-   根據預設，連接埠繫結檔案永遠會包含定義雙向傳送埠。 當您匯入 BizTalk 應用程式中的這個檔案時，它會建立雙向傳送埠。 不過，您可能有單向傳送埠的協調流程。 因此，當您設定協調流程，並使用 匯入繫結檔案所建立的連接埠，連接埠不在清單中。 這是因為您建立的協調流程一部分的邏輯連接埠是單向連接埠在協調流程中建立的實體通訊埠是雙向的連接埠。 在這種情況下，您可以編輯繫結檔案，進行下列變更：  
  
    |如需|執行方式|  
    |--------------|-------------|  
    |若要編輯連接埠繫結檔案，以設定單向傳送埠|-在下列摘錄中，將值變更**IsTwoWay**屬性**false**。 最初，這個值設定為**true**。<br /><br /> `<SendPort Name="port_name" IsStatic="true" IsTwoWay="false" BindingOption="0">`<br /><br /> -註解下列區段：<br /><br /> `<ReceivePipeline Name="Microsoft.BizTalk.DefaultPipelines.XMLReceive"    FullyQualifiedName="Microsoft.BizTalk.DefaultPipelines.XMLReceive,    Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral,    PublicKeyToken=token" Type="1" TrackingOption="None" Description=""/>`<br /><br /> `<ReceivePipelineData xsi:nil="true" />`|  
  
## <a name="configuring-a-wcf-siebel-port-using-the-port-binding-file-generated-using-consume-adapter-service-add-in"></a>設定使用連接埠繫結檔案使用所產生的 Wcf-siebel 埠取用配接器服務增益集  
 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立連接埠繫結檔案，您可以匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您可以使用相同的連接埠繫結檔案，同時建立 BizTalk WCF Siebel 中的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 不過，在建立 Wcf-siebel 連接埠之前，您必須執行下列工作來修改連接埠繫結檔案。  
  
1.  在文字編輯器中開啟連接埠繫結檔案。  
  
2.  搜尋並新增 Wcf-siebel 配接器中的名稱取代 「 WCF 自訂 」[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 例如，如果您新增 Wcf-siebel 配接器，當做"SiebelAdapter"，取代 「 WCF 自訂 」 與 「 SiebelAdapter"。  
  
3.  搜尋"ConfigurationClsid"屬性，並取代現有屬性的值"7971A78D-AE8F-42B4-834D-3A957FD945E9"。  
  
4.  儲存並關閉繫結檔案。  
  
5.  匯入繫結檔案中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 請參閱[重複使用 Siebel 配接器中的配接器繫結](../../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md)。 
  
## <a name="see-also"></a>另請參閱  
若要建立 Siebel 的 BizTalk 應用程式 [建置組塊 

配接器] (.../../ adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md）