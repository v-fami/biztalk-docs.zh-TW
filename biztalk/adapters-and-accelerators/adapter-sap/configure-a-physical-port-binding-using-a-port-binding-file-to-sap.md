---
title: 設定使用連接埠繫結檔案至 SAP 的實體連接埠繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- port binding file
- physical port binding, configuring using a port binding file
ms.assetid: c637971c-3ecd-4026-8f74-bd5173774438
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a80eeae5a71ca66f2bfb53bfc33f15d7d041203b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002111"
---
# <a name="configure-a-physical-port-binding-using-a-port-binding-file-to-sap"></a>設定實體連接埠繫結使用的連接埠繫結檔案至 SAP
當您使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生 SAP 成品，以外的結構描述檔案的中繼資料[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會產生的連接埠繫結檔案。 您可以將此繫結檔案匯 BizTalk 應用程式建立實體傳送或接收埠。 [重複使用 SAP 配接器繫結](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)包含匯入繫結檔案的步驟。 如果您匯入此繫結檔案時，您不必以手動方式建立實體傳送或接收埠。  
  
> [!IMPORTANT]
>  同時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，如果您未指定的字串類型的繫結屬性的值，而其預設值是 null，則該屬性繫結將無法使用繫結檔案中。 您必須手動加入的繫結屬性和其值在繫結檔案中，如有必要。  
  
 建立一律使用連接埠繫結檔案的連接埠建立雙向傳送埠或接收埠。 如果您想要建立單向連接埠，您可以建立它以手動方式使用的步驟[手動設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)。 或者，您可以遵循本主題，以修改要建立單向連接埠的連接埠繫結檔案所述的因應措施。  
  
> [!IMPORTANT]
>  使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]不會建立使用您可以建立的 WCF SAP 連接埠的連接埠繫結檔案。 不過，您可以進行一些變更連接埠繫結檔案所產生[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]並用它來建立 WCF SAP 連接埠。 如需詳細資訊，請參閱 <<c0> [ 設定 WCF SAP 連接埠繫結檔案產生使用取用配接器服務增益集的連接埠使用](#BKMK_add_wcf_sap)。  
  
 以下是您必須了解所產生的繫結檔案相關的一些重要事項[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]:  
  
-   建立的檔案是具有特定命名慣例。 如果您產生輸出作業，也就是將訊息傳送至 SAP 系統，中繼資料檔案的名稱會是 WcfSendPort_SAPBinding_Custom.bindinginfo.xml。  
  
     如果您產生作業的中繼資料輸入，也就是從 SAP 系統接收訊息，檔案的名稱會是 WcfReceivePort_SAPBinding_Custom.bindinginfo.xml。  
  
-   檔案包含繫結組態、 繫結型別、 端點 URI 和中繼資料所產生的作業為基礎的連接埠動作的相關資訊。 當您匯入此繫結檔案，若要建立的連接埠時，若要設定實體連接埠所需的所有相關資訊會自動設定的連接埠。  
  
    > [!IMPORTANT]
    >  根據預設，傳送埠上的動作會對應至您要為其產生中繼資料的作業名稱。 比方說，如果您為 RFC_CUSTOMER_GET 產生中繼資料，在連接埠上的動作設定為`<Operation Name="RFC_CUSTOMER_GET" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET " />`。 不過，您在 BizTalk 協調流程中建立邏輯傳送連接埠上的作業名稱可能不會相同。 您必須確定作業中的名稱 （在 BizTalk 協調流程） 的邏輯連接埠與實體傳送埠 （在 BizTalk Server 管理主控台） 都相同。 如果沒有，您會收到錯誤時將訊息傳送至 SAP 系統，透過傳送埠。  
  
-   您只需要提供認證來連接到 SAP 系統的連接埠。 繫結檔案會保留用來連接的使用者名稱，而基於安全性的繫結檔案不包含密碼。  
  
## <a name="key-considerations-for-using-the-port-binding-file"></a>使用連接埠繫結檔案的重要考量  
  
-   當您匯入繫結檔案時，您可能會看到對話方塊訊息，通知的 BizTalk 應用程式名稱，繫結檔案中的不符合您要匯入繫結檔案的應用程式名稱。 您可以放心地忽略此訊息，並繼續。  
  
-   繫結檔案也包含名稱的連接埠和接收位置。 如果您要匯入繫結檔案的 BizTalk 應用程式建立連接埠或接收位置具有相同名稱做為現有的連接埠在相同的 BizTalk 應用程式中，您會收到錯誤。 您必須手動編輯繫結檔案來指定唯一的名稱，連接埠或接收位置。  
  
-   繫結檔案也包含連線 URI 的相關資訊。 如果繫結檔案會建立具有相同的接收 URI 相同的 BizTalk 應用程式中的現有接收位置的接收位置，您會收到錯誤。 您必須手動編輯繫結檔案來指定唯一的 URI。  
  
-   根據預設，連接埠繫結檔案一定會包含定義雙向連接埠 （傳送或接收）。 當您匯入 BizTalk 應用程式中的這個檔案時，它會建立雙向傳送或接收埠。 不過，您可能有協調流程具有單向傳送或接收埠。 因此，當您設定這類協調流程，並使用 匯入繫結檔案所建立的連接埠，連接埠不在清單中。 這是因為您建立的協調流程的邏輯連接埠是單向連接埠，而協調流程中建立的實體連接埠是雙向的連接埠。 在此情況下，您可以編輯繫結檔案，進行下列變更：  
  
    |如需|執行方式|  
    |--------------|-------------|  
    |若要編輯的連接埠繫結檔案，以設定單向傳送埠|1.在下列摘錄中，將值變更**IsTwoWay**屬性設**false**。 一開始，此值設為 **，則為 true**。<br />     `<SendPort Name="port_name" IsStatic="true" IsTwoWay="false" BindingOption="0">`<br />2.註解下列摘錄：<br />     `<ReceivePipeline Name="Microsoft.BizTalk.DefaultPipelines.XMLReceive"    FullyQualifiedName="Microsoft.BizTalk.DefaultPipelines.XMLReceive,    Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral,    PublicKeyToken=token" Type="1" TrackingOption="None" Description=""/>`<br />     `<ReceivePipelineData xsi:nil="true" />`|  
    |若要編輯的連接埠繫結檔案，以設定單向接收埠|1.在下列摘錄中，將值變更**IsTwoWay**屬性設**false**。 一開始，此值設為 **，則為 true**。<br />     `<ReceivePort Name="port_name" IsTwoWay="false" BindingOption="1">`<br />2.註解下列摘錄：<br />     `<SendPipeline Name="Microsoft.BizTalk.DefaultPipelines.XMLTransmit"    FullyQualifiedName="Microsoft.BizTalk.DefaultPipelines.XMLTransmit,    Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral,    PublicKeyToken=token" Type="2" TrackingOption="None" Description="" />`<br />     `<SendPipelineData xsi:nil="true" />`<br />     `<SendPipelineData xsi:nil="true" />`|  
  
##  <a name="BKMK_add_wcf_sap"></a> 設定使用連接埠繫結檔案，使用所產生的 WCF SAP 連接埠使用配接器服務增益集  
 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立連接埠繫結檔案，您可以匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您可以使用相同的連接埠繫結檔案，同時建立中的 BizTalk WCF SAP 連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 不過，建立 WCF SAP 連接埠之前，您必須執行下列工作來修改連接埠繫結檔案。  
  
1. 在文字編輯器中開啟連接埠繫結檔案。  
  
2. 搜尋並新增中的 WCF SAP 配接器名稱取代 「 WCF 自訂 」[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 比方說，如果您新增為 「 SAPAdapter"WCF-SAP 配接器，來取代 「 WCF 自訂 」 與 「 SAPAdapter"。  
  
3. 搜尋"ConfigurationClsid 」 屬性，並取代"A5F15999-8879-472d-8C62-3B5EA9406504 」 中的現有屬性的值。  
  
4. 儲存並關閉 繫結檔案。  
  
5. 匯入繫結檔案中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 [重複使用 SAP 配接器繫結](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)列出的步驟。
  
## <a name="see-also"></a>另請參閱  
[建立 SAP 應用程式的建構元素](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)