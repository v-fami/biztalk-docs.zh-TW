---
title: 如何匯出 EDI-AS2 解決方案的繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 856ab630-66c4-4496-884a-fdbe641143c5
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c36bd9c265d28555c40f84f1728fd28846fbd516
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012327"
---
# <a name="how-to-export-bindings-for-an-edi-as2-solution"></a>如何匯出 EDI-AS2 解決方案的繫結
本主題說明如何從設定為 EDI 和 (或) AS2 方案的電腦匯出組態。 這可讓您以自動化的方式在另一部電腦上設定相同的組態。 您可以從應用程式、群組或組件匯出繫結。  
  
 您可以在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台內建立繫結檔案。 .xml 繫結檔案包含所有與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態有關的資訊。 這包括所有的 EDI 和 AS2 組態屬性，但是不包含某些安全性資訊。 如需繫結檔案 （包括 EDI 和 AS2 節點） 中的節點的詳細資訊，請參閱[繫結檔案的結構](../core/structure-of-a-binding-file.md)。 如需 EDI/AS2 繫結的一般資訊，請參閱下面的「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 繫結檔案中的 EDI 和 AS2 節點」。  
  
 您也可以使用 .msi 檔，在匯出應用程式時一併匯出繫結。 如需詳細資訊，請參閱 <<c0> [ 如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。 或者，您可以使用 BTSTask 命令匯出和匯入繫結。 如需 BTSTask 的詳細資訊，請參閱[BTSTask 命令列參考](../core/btstask-command-line-reference.md)。  
  
 **匯出繫結**  
  
 在您匯出組態時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會自動匯出所有繫結合作對象的 EDI 屬性和其他合作對象資訊。 如果您啟動匯出全域合作對象資訊的功能，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 也會匯出未繫結到協調流程之合作對象的屬性，以及全域 EDI 屬性。 您可以利用三種方法來匯出全域合作對象資訊：  
  
- 在 [匯出繫結] 對話方塊中核取 [匯出全域合作對象資訊] 屬性。  
  
- 在 [匯出 MSI 檔案精靈] 的 [選取資源] 窗格中核取 [全域合作對象] 核取方塊。  
  
- 在 BTSTask 命令列工具中使用 GlobalParties 參數，如下所示：  
  
  ```  
  BTSTask ExportBindings -Destination:value ((([-ApplicationName:value] | [-AssemblyName:value]) [-GlobalParties]) | [-GroupLevel])  
  ```  
  
  基於安全性理由，當您匯出繫結檔案，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]從檔案移除繫結密碼。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ISA1、 ISA2、 ISA3 和 ISA4 欄位從 X12 與 EDIFACT 屬性移除 UNB6.1 和 UNB6.2 欄位屬性。  
  
  除了使用 export-bindings、export-application 或 BTSTask 命令之外，您也可以手動建立 XML 繫結檔案。 透過這種方式，您可以從企業營運系統應用程式匯出合作對象和 EDI 設定。 接著，您就可以使用 import-bindings 命令或 BTSTask 命令來匯入繫結。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組成員的帳戶來登入。 如需詳細資訊，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的＜部署和管理 BizTalk 應用程式所需的權限＞。  
  
### <a name="exporting-the-configuration-into-a-binding-file"></a>將組態匯出到繫結檔案  
  
1. 在您要匯出組態的來源電腦上，開啟 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。  
  
2. 以滑鼠右鍵按一下您想要複製的組態，指向 BizTalk 應用程式**匯出**，然後按一下**繫結**。  
  
   > [!NOTE]
   >  您也可以使用 BTSTask 公用程式匯出或匯入組態。  
  
3. 選取匯出選項，包括選擇從目前的應用程式或群組匯出，或是匯出組件的繫結。  
  
4. 如果您想要匯出所有合作對象，且其不區分內容，即使協調流程未繫結，然後按一下**匯出全域合作對象資訊**。  
  
   > [!NOTE]
   >  如果您沒有按一下**匯出全域合作對象資訊**，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]匯出繫結至協調流程至繫結檔案的任何合作對象屬性。 不過，它不會匯出任何合作對象未繫結至協調流程，除非您按一下 **匯出全域合作對象資訊**。  
   > 
   > [!NOTE]
   >  產生的繫結檔案時**匯出全域合作對象資訊**選取屬性會包含在電腦上定義的所有合作對象的設定。 在電腦定義的一組合作對象中，您將無法匯出其中一部分子集的組態。  
  
5. 按一下 **確定**匯出繫結。  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不會匯出任何 EDI 機密欄位，例如密碼或安全性/驗證資訊。 對於任何 EDI 機密欄位，它都會匯出空白字串。 將繫結匯入至另一部電腦之後，您必須手動設定 EDI 機密欄位的值。  
  
6. 手動記錄所有的 EDI 機密欄位，例如密碼或安全性/驗證資訊，以便稍後在匯入繫結的目標電腦上進行設定。  
  
## <a name="edi-and-as2-nodes-in-the-biztalk-server-binding-file"></a>BizTalk Server 繫結檔案中的 EDI 和 AS2 節點  
 如果您匯出組態**匯出全域合作對象資訊**屬性選取，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會產生繫結檔案具有下列節點：  
  
```  
EdiData  
   PartyEDIProperties  
      PartnerAgreement  
         Contacts  
      PartnerEdifact  
         PartnerEdifactReceiverGroups  
         PartnerEdifactSenderGroups  
      PartnerAckValidation  
      PartnerX12  
      PartnerX12ReceiverGroups  
      PartnerX12SenderGroups  
      PartnerBatchUpdatable  
      PartnerAS2CommonUpdatable  
      PartnerAS2  
```  
  
 EDI 全域屬性將會加入至繫結檔案的下列節點中。  
  
```  
EDIGlobalProperties  
   EDIGlobalProperties  
      GlobalCommon  
      GlobalEdiFact  
      GlobalX12  
```  
  
 EDI 和 AS2 節點會加入至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 繫結檔案的結尾。 EdiData 節點會加入至 [合作對象集合] 節點底下的 [合作對象] 子節點，而且 EdiGlobalProperties 節點會加入 [合作對象集合] 後面 (與其位於相同層級)。 如需 BizTalk 繫結檔案中 EDI 和 AS2 節點的詳細資訊，請參閱[繫結檔案的結構](../core/structure-of-a-binding-file.md)。  
  
 EdiData 節點是選用項目。 不過，如果有 EdiData 節點存在，則 EdiData 底下必須有子節點。 同樣地，EdiGlobalProperties 節點也是選用項目，但是如果有 EdiGlobalProperties 存在，其底下也必須有子節點。  
  
 EDI 和 AS2 繫結檔案節點不會直接對應到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中夥伴協議管理員的屬性頁。 某些 EDI 和 AS2 繫結檔案節點包括用於傳送者角色的屬性，以及用於接收者角色的屬性。 角色是由節點中的 IsSender 屬性指定。 如果節點並未用於傳送者和接收者兩種角色 (PartnerAgreement、PartnerBatchUpdatable、PartnerAS2Updatable 和 GlobalCommon)，則 IsSender 一定是 False。  
  
 不論 IsSender 設定為 True 或 False，PartnerEdifact 和 PartnerX12 節點都會包含用於接收者和傳送者兩種角色的屬性。 例如，即使 IsSender 是 True，PartnerEdifact 也會包含 Una1 欄位 (用於做為交換接收者的合作對象)， 而即使 IsSender 是 False，PartnerEdifact 還是會包含 Unb5CheckDup 欄位 (用於做為交換傳送者的合作對象)。 不過，當 IsSender 是 True 時，做為交換接收者之合作對象的欄位就不會在 UI 或引擎中使用，而會指定預設值。 同樣地，當 IsSender 為 False，做為交換傳送者合作對象的欄位不會在 UI 或引擎，但會提供預設值。  
  
 如果屬性的預設值是空值，除非該欄位已指定值，否則便不會包含在繫結檔案中。  
  
 繫結檔案資料會儲存在 BizTalk 管理資料庫 (BizTalkMgmtDb) 的資料表中。