---
title: 設定實體連接埠繫結使用的連接埠繫結檔案至 Oracle E-business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5c3c468e-815c-4611-879c-8da9111eeb3b
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15ab173c8950e3a86d8f68abf5e84d821b2b38d1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996527"
---
# <a name="configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-e-business-suite"></a>設定實體連接埠繫結使用的連接埠繫結檔案至 Oracle E-business Suite
當您使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來產生結構描述檔以外的 Oracle E-business Suite 構件的中繼資料[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會產生的連接埠繫結檔案。 您可以將此繫結檔案匯 BizTalk 應用程式建立實體傳送或接收埠。 如需匯入繫結檔案的指示，請參閱 <<c0> [ 重複使用與 Oracle E-business Suite 配接器繫結](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)。 如果您匯入此繫結檔案時，您不必以手動方式建立實體傳送或接收埠。  
  
> [!IMPORTANT]
>  同時使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，如果您未指定的字串類型的繫結屬性的值，而其預設值是 null，則該屬性繫結將無法使用繫結檔案中。 您必須手動加入的繫結屬性和其值在繫結檔案中，如有必要。  
  
 建立一律使用連接埠繫結檔案的連接埠建立雙向傳送埠或單向接收埠。 如果您想要建立單向傳送埠，您可以建立它以手動方式遵循所述的程序[手動設定實體連接埠繫結來 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。 或者，您可以遵循本主題，以修改要建立單向傳送埠的連接埠繫結檔案所述的因應措施。  
  
> [!NOTE]
>  輸入的作業，繫結檔案的連接埠一律會建立單向接收埠。 這是因為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]僅支援單向接收埠的輸入操作。  
> 
> [!IMPORTANT]
>  使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]不會建立使用您可以建立 Wcf-oracleebs 連接埠的連接埠繫結檔案。 不過，您可以進行一些變更連接埠繫結檔案所產生[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]並用它來建立 Wcf-oracleebs 的連接埠。 如需詳細資訊，請參閱 < [Wcf-oracleebs 連接埠繫結檔案產生使用取用配接器服務增益集的連接埠使用設定](#BKMK_ModifyBinding)。  
  
 以下是您必須了解繫結相關的一些重點檔[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會產生：  
  
- 建立的檔案是具有特定命名慣例。 如果您產生輸出作業的中繼資料，也就是將訊息傳送至 Oracle E-business Suite，檔案的名稱是 WcfSendPort_OracleEBSBinding_Custom.bindinginfo.xml。  
  
   如果您產生的輸入作業的中繼資料，也就是檔案的從 Oracle E-business Suite，接收訊息名稱是檔案的 WcfReceivePort_OracleEBSBinding_Custom.bindinginfo.xml。  
  
- 檔案包含繫結組態、 繫結型別、 端點 URI 和中繼資料所產生的作業為基礎的連接埠動作的相關資訊。 當您將此繫結檔案匯 BizTalk 應用程式建立的連接埠時，若要設定實體連接埠所需的所有相關資訊會自動設定連接埠。  
  
  > [!IMPORTANT]
  >  根據預設，傳送埠上的動作會對應至您要為其產生中繼資料的作業名稱。 例如，如果您產生介面資料表 (例如 FA_BOOKS) 上的插入作業的中繼資料時，連接埠上的動作設定為`<Operation Name="Insert" Action="InterfaceTables/Insert/OFA/FA/FA_BOOKS" />`。 不過，您在 BizTalk 協調流程中建立邏輯傳送連接埠上的作業名稱可能不會相同。 您必須確定作業中的名稱的邏輯傳送連接埠 （在 BizTalk 協調流程），以及實體傳送埠 (在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台) 相同。 如果沒有，您會收到錯誤時將訊息傳送至 Oracle E-business Suite 中，透過傳送埠。  
  
- 您只需要提供認證來連接到 Oracle E-business Suite 的連接埠。 雖然在繫結檔案會保留用來連接，基於安全性的繫結檔案不包含密碼的使用者名稱。  
  
## <a name="key-considerations-for-using-the-port-binding-file"></a>使用連接埠繫結檔案的重要考量  
  
- 當您匯入繫結檔案時，您可能會看到對話方塊訊息，通知的 BizTalk 應用程式名稱，繫結檔案中的不符合您要匯入繫結檔案的應用程式名稱。 您可以放心地忽略此訊息，並繼續。  
  
- 繫結檔案也包含名稱的連接埠和接收位置。 如果您要匯入繫結檔案的 BizTalk 應用程式建立連接埠或接收位置具有相同名稱做為現有的連接埠在相同的 BizTalk 應用程式中，您會收到錯誤。 您必須手動編輯繫結檔案來指定唯一的名稱，連接埠或接收位置。  
  
- 繫結檔案也包含連線 URI 的相關資訊。 如果繫結檔案會建立具有相同的接收 URI 相同的 BizTalk 應用程式中的現有接收位置的接收位置，您會收到錯誤。 您必須手動編輯繫結檔案來指定唯一的 URI。  
  
- 根據預設，輸出作業的連接埠繫結檔案一律會包含定義雙向傳送埠。 當您匯入 BizTalk 應用程式中的這個檔案時，它會建立雙向傳送埠。 不過，您可能有單向傳送埠的協調流程。 因此，當您設定這類協調流程，並使用 匯入繫結檔案所建立的連接埠，連接埠不在清單中。 這是因為您建立的協調流程的邏輯連接埠是單向連接埠，而協調流程中建立的實體連接埠是雙向的連接埠。 在此情況下，您可以編輯此繫結檔案，進行下列變更：  
  
  |如需|執行方式|  
  |--------------|-------------|  
  |若要編輯的連接埠繫結檔案，來設定單向傳送埠|1.在下列摘錄中，將值變更**IsTwoWay**屬性設**false**。 一開始，此值設為 **，則為 true**。<br />     `<SendPort Name="port_name" IsStatic="true" IsTwoWay="false " BindingOption="0">`<br />2.註解下列摘錄：<br />     `<ReceivePipeline Name="Microsoft.BizTalk.DefaultPipelines.XMLReceive"   FullyQualifiedName="Microsoft.BizTalk.DefaultPipelines.XMLReceive,   Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral,   PublicKeyToken= token" Type="1" TrackingOption="None" Description=""/>`<br />     `<ReceivePipelineData xsi:nil="true" />`|  
  
  > [!IMPORTANT]
  >  輸入的作業，繫結檔案的連接埠一律會建立單向接收埠。 這是因為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]僅支援單向接收埠的輸入操作。  
  
##  <a name="BKMK_ModifyBinding"></a> 設定使用連接埠繫結檔案，產生使用 Wcf-oracleebs 連接埠使用配接器服務增益集  
 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會建立連接埠繫結檔案，您可以匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您可以使用相同的連接埠繫結檔案，同時建立中的 BizTalk Wcf-oracleebs 連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 不過，建立 Wcf-oracleebs 連接埠之前，您必須執行下列工作來修改連接埠繫結檔案。  
  
1. 在文字編輯器中開啟連接埠繫結檔案。  
  
2. 搜尋並新增 Wcf-oracleebs 配接器名稱取代 「 WCF 自訂 」[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 比方說，如果您新增 Wcf-oracleebs 配接器，為 「 OracleEBSAdapter 」，來取代 「 WCF 自訂 」 與 「 OracleEBSAdapter"。  
  
3. 搜尋"ConfigurationClsid 」 屬性，並取代"F452BB15-7A0D-495d-9395-C630D3FD29CD 」 中的現有屬性的值。  
  
4. 儲存並關閉 繫結檔案。  
  
5. 匯入繫結檔案中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需有關如何匯入繫結檔案的指示，請參閱 <<c0> [ 重複使用與 Oracle E-business Suite 配接器繫結](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)。  
  
## <a name="see-also"></a>另請參閱  
[若要建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)