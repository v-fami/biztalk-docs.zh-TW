---
title: 設定 Oracle E-business Suite 中使用訊息內容屬性的應用程式內容 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51b76788-5c81-4bb4-8ef6-b1439955ea97
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71920920c11028adb1f699e3faee463876399b36
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003999"
---
# <a name="configure-the-application-context-using-message-context-properties-in-oracle-e-business-suite"></a>設定 Oracle E-business Suite 中使用訊息內容屬性的應用程式內容
若要使用的 Oracle E-business Suite 成品上執行作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須適當設定的應用程式內容。 您可以透過下列方式設定應用程式內容：  
  
- 藉由指定配接器所公開的繫結屬性。 如需詳細資訊，請參閱 <<c0> [ 設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
- 使用配接器所公開的訊息內容屬性。 使用訊息內容屬性中設定應用程式內容時，您必須考慮下列。  
  
  -   您可以設定值，僅適用於**ApplicationShortName**， **OrganizationID**， **ResponsibilityKey**，以及**ResponsibilityName**使用訊息內容屬性。 使用者名稱和密碼，您必須使用的繫結屬性。 指定的值**ResponsibilityKey**訊息內容屬性會覆寫的指定值**ResponsibilityName**訊息內容屬性。  
  
  -   如果您設定應用程式內容使用繫結屬性和訊息內容屬性，指定訊息內容屬性的值更高的優先順序，並覆寫指定的繫結屬性的值。 不過，比方說，如果您指定的應用程式簡短名稱，為訊息內容屬性，以及組織識別碼和責任名稱做為繫結屬性時，只有應用程式的簡短名稱的值是取自訊息內容屬性。 其餘部分會挑選從相關的繫結屬性。  
  
  為何要使用訊息內容屬性，透過繫結來設定應用程式內容的屬性？ 如果您設定應用程式內容繫結屬性，Wcf-custom 傳送埠[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可用僅適用於特定的組織識別碼、 責任和您指定的繫結屬性的應用程式。 相反的如果您使用訊息內容屬性，您可以設定 「 一般 」 的 Wcf-custom 傳送埠，並在訊息層級設定的應用程式內容。  
  
  配接器用戶端必須設定訊息內容屬性傳送到 Oracle E-business Suite 來叫用 Oracle E-business suite 作業的訊息。 中的訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]是固定不變。 因此，用戶端必須先從現有的訊息，建立一則訊息，然後將訊息內容屬性在新的訊息。 在本節中所述的程序，假設現有的訊息，會呼叫**要求**，而新的訊息稱為**New_Request**。  
  
## <a name="set-the-message-context-properties-for-biztalk-applications"></a>設定訊息的 BizTalk 應用程式的內容屬性  
  
1. 開啟 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
2. 在 [方案總管] 中，以滑鼠右鍵按一下**參考**，然後按一下**新增參考**。  
  
3. 在**加入參考** 對話方塊中，按一下**瀏覽**索引標籤，然後再瀏覽至位置，BizTalk 屬性結構描述 DLL 的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可用。  
  
    此 DLL `Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll`，會安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]在\<*安裝磁碟機*\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\bin。  
  
4. 選取 DLL，然後再按一下**新增**。  
  
5. 在 BizTalk 協調流程中，將訊息，新增**New_Request**。 針對**訊息類型**屬性，請確定您選取相同的型別做為現有的要求訊息。  
  
6. 「 傳送 」 圖形之前使用訊息傳送至傳送埠中，新增 「 建構訊息 」 圖形，並在其中，「 訊息指派 」 圖形。  
  
7. 按兩下訊息指派圖形，以開啟**BizTalk 運算式編輯器**。  
  
8. 在  **BizTalk 運算式編輯器**，新增下列程式碼，然後按一下 **確定**:  
  
   ```  
   New_Request = Request;  
   New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ApplicationShortName) = "AR";  
   New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ResponsibilityKey) = "RECEIVABLES_VISION_OPERATIONS";  
   New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ResponsibilityName) = "Receivables, Vision Operations (USA)";  
   New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.OrganizationId) = "204";  
   ```  
  
   > [!IMPORTANT]
   >  指定的值**ResponsibilityKey**訊息內容屬性會覆寫的指定值**ResponsibilityName**訊息內容屬性。  
  
9. 請確定協調流程進一步處理是藉由使用**New_Request**訊息。  
  
10. 您可以部署在此協調流程之前[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須將組件參考新增`Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll`中，您會部署 「 協調流程的 BizTalk 應用程式。 若要部署中的組件[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]:  
  
    1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
    2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，，然後您要新增 BizTalk 組件的應用程式。  
  
    3. 您可以要求您想要的資料表**做為回應的一部分傳回。  
  
    4. 在 [**新增資源**] 對話方塊中，按一下**新增**，瀏覽至包含 BizTalk 組件檔案，也就是資料夾\<*安裝磁碟機*\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\bin。 選取 `Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll`檔案，然後再按一下**開啟**。  
  
    5. 在 **選項**索引標籤上，指定 BizTalk 組件安裝到全域組件快取 (GAC) 的選項，然後按一下**確定**。  
  
## <a name="set-the-language-for-performing-operations"></a>設定執行作業的語言  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援 Oracle E-business Suite、 多國語言支援 (MLS) 功能，並可讓您在執行作業時指定的語言。 配接器會公開**語言**訊息內容屬性來指定執行作業的語言。  
  
 指定的值**語言**訊息內容屬性會覆寫的值**語言**下的屬性繫結**MlsSettings**繫結屬性。 如需詳細資訊**MlsSettings**繫結屬性，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
