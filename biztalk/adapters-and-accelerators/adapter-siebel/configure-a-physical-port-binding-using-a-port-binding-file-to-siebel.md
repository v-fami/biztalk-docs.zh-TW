---
title: 設定實體連接埠繫結使用的連接埠繫結檔案至 Siebel |Microsoft Docs
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
ms.openlocfilehash: 36b5def2e4cca694e63040cfc8721be3a8819222
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966871"
---
# <a name="configure-a-physical-port-binding-using-a-port-binding-file-to-siebel"></a>設定實體連接埠繫結使用的連接埠繫結檔案至 Siebel
當您使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生 Siebel 成品，以外的結構描述檔案的中繼資料[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會產生的連接埠繫結檔案。 您可以將此繫結檔案匯 BizTalk 應用程式建立實體傳送埠。 請參閱[重複使用 Siebel 配接器中的配接器繫結](../../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md)。 如果您匯入此繫結檔案時，您不必以手動方式建立實體傳送埠。  
  
> [!IMPORTANT]
>  同時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，如果您未指定的字串類型的繫結屬性的值，而其預設值是 null，則該屬性繫結將無法使用繫結檔案中。 您必須手動加入的繫結屬性和其值在繫結檔案中，如有必要。  
  
 建立一律使用連接埠繫結檔案的連接埠，會建立雙向傳送埠。 如果您想要建立單向連接埠，您可以建立它以手動方式所遵循的步驟[設定的實體連接埠繫結使用的連接埠繫結檔案至 Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md)。 或者，您可以遵循本主題，以修改要建立單向連接埠的連接埠繫結檔案所述的因應措施。  
  
> [!IMPORTANT]
>  使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]不會建立使用您可以建立 Wcf-siebel 連接埠的連接埠繫結檔案。 不過，您可以進行一些變更連接埠繫結檔案所產生[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]並用它來建立 WCF Siebel 的連接埠。 如需詳細資訊，請參閱設定 Wcf-siebel 連接埠繫結檔案產生使用取用配接器服務增益集的連接埠使用。  
  
 以下是您必須了解所產生的繫結檔案相關的一些重要事項[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]:  
  
-   建立的檔案是具有特定命名慣例。 如果您產生輸出作業，也就是將訊息傳送至 Siebel 系統，中繼資料檔案的名稱是 WcfSendPort_SiebelBinding_Custom.bindinginfo.xml。  
  
-   檔案包含繫結組態、 繫結型別、 端點 URI 和中繼資料所產生的作業為基礎的連接埠動作的相關資訊。 當您匯入此繫結檔案，若要建立的連接埠時，若要設定實體連接埠所需的所有相關資訊會自動設定的連接埠。  
  
    > [!IMPORTANT]
    >  根據預設，傳送埠上的動作會對應至您要為其產生中繼資料的作業名稱。 例如，如果您產生帳戶商務元件上的插入作業的中繼資料時，連接埠上的動作設定為`<Operation Name="Insert" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert " />`。 不過，您在 BizTalk 協調流程中建立邏輯傳送連接埠上的作業名稱可能不會相同。 您必須確定作業中的名稱 （在 BizTalk 協調流程） 的邏輯連接埠與實體傳送埠 （在 BizTalk Server 管理主控台） 都相同。 如果沒有，您會收到錯誤時將訊息傳送至傳送埠透過 Siebel 系統。  
  
-   您只需要提供認證來連接到 Siebel 系統的連接埠。 繫結檔案會保留用來連接的使用者名稱，而基於安全性的繫結檔案不包含密碼。  
  
## <a name="key-considerations-for-using-the-port-binding-file"></a>使用連接埠繫結檔案的重要考量  
  
-   當您匯入繫結檔案時，您可能會看到對話方塊訊息，通知的 BizTalk 應用程式名稱，繫結檔案中的不符合您要匯入繫結檔案的應用程式名稱。 您可以放心地忽略此訊息，並繼續。  
  
-   繫結檔案也包含名稱的連接埠和接收位置。 如果您要匯入繫結檔案的 BizTalk 應用程式建立連接埠或接收位置具有相同名稱做為現有的連接埠在相同的 BizTalk 應用程式中，您會收到錯誤。 您必須手動編輯繫結檔案來指定唯一的名稱，連接埠或接收位置。  
  
-   根據預設，連接埠繫結檔案一律會包含定義雙向傳送埠。 當您匯入 BizTalk 應用程式中的這個檔案時，它會建立雙向傳送埠。 不過，您可能有單向傳送埠的協調流程。 因此，當您設定這類協調流程，並使用 匯入繫結檔案所建立的連接埠，連接埠不在清單中。 這是因為您建立的協調流程的邏輯連接埠是單向連接埠，而協調流程中建立的實體連接埠是雙向的連接埠。 在此情況下，您可以編輯繫結檔案，進行下列變更：  
  
    |如需|執行方式|  
    |--------------|-------------|  
    |若要編輯的連接埠繫結檔案，以設定單向傳送埠|-在下列摘錄中，將值變更**IsTwoWay**屬性設**false**。 一開始，此值設為 **，則為 true**。<br /><br /> `<SendPort Name="port_name" IsStatic="true" IsTwoWay="false" BindingOption="0">`<br /><br /> -標記為註解下列摘錄：<br /><br /> `<ReceivePipeline Name="Microsoft.BizTalk.DefaultPipelines.XMLReceive"    FullyQualifiedName="Microsoft.BizTalk.DefaultPipelines.XMLReceive,    Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral,    PublicKeyToken=token" Type="1" TrackingOption="None" Description=""/>`<br /><br /> `<ReceivePipelineData xsi:nil="true" />`|  
  
## <a name="configuring-a-wcf-siebel-port-using-the-port-binding-file-generated-using-consume-adapter-service-add-in"></a>設定使用連接埠繫結檔案，產生使用 Wcf-siebel 連接埠使用配接器服務增益集  
 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立連接埠繫結檔案，您可以匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您可以使用相同的連接埠繫結檔案，同時建立中的 BizTalk Wcf-siebel 連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 不過，建立 WCF Siebel 連接埠之前，您必須執行下列工作來修改連接埠繫結檔案。  
  
1. 在文字編輯器中開啟連接埠繫結檔案。  
  
2. 搜尋並新增 Wcf-siebel 配接器名稱取代 「 WCF 自訂 」[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 比方說，如果您新增 Wcf-siebel 配接器，為 「 SiebelAdapter 」，來取代 「 WCF 自訂 」 與 「 SiebelAdapter"。  
  
3. 搜尋"ConfigurationClsid 」 屬性，並取代"7971A78D-AE8F-42B4-834D-3A957FD945E9 」 中的現有屬性的值。  
  
4. 儲存並關閉 繫結檔案。  
  
5. 匯入繫結檔案中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 請參閱[重複使用 Siebel 配接器中的配接器繫結](../../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md)。 
  
## <a name="see-also"></a>另請參閱  
[建置組塊來建立 Siebel BizTalk 應用程式 

配接器] (../../ adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md）