---
title: "設定 Oracle E-business Suite 中使用訊息內容屬性的應用程式內容 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51b76788-5c81-4bb4-8ef6-b1439955ea97
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43f0128b0d1da7ddfb9a29b697d5d5073f69dd33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-application-context-using-message-context-properties-in-oracle-e-business-suite"></a>設定 Oracle E-business Suite 中使用訊息內容屬性的應用程式內容
若要使用的 Oracle E-business Suite 成品上執行作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，則必須適當設定的應用程式內容。 您可以下列方式來設定應用程式內容：  
  
-   藉由指定配接器會公開繫結屬性。 如需詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
-   使用配接器會公開的訊息內容屬性。 使用訊息內容屬性中設定應用程式內容時，您必須考慮下列。  
  
    -   您可以設定僅適用於值**ApplicationShortName**， **OrganizationID**， **ResponsibilityKey**，和**ResponsibilityName**使用訊息內容屬性。 使用者名稱和密碼，您必須使用的繫結屬性。 指定的值**ResponsibilityKey**訊息內容屬性會覆寫指定的值**ResponsibilityName**訊息內容屬性。  
  
    -   如果您設定應用程式內容使用繫結屬性和訊息內容屬性，指定訊息內容屬性的值會優先，以及覆寫指定的繫結屬性的值。 不過，比方說，如果您指定的應用程式的簡短名稱做為訊息內容屬性，以及組織識別碼與責任名稱做為繫結屬性時，應用程式的簡短名稱的值是取自訊息內容屬性。 其餘部分會從相關的繫結屬性中選取。  
  
 為什麼要透過繫結來設定應用程式內容的屬性使用訊息內容屬性？ 如果您設定應用程式內容繫結屬性，Wcf-custom 傳送埠[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可用僅適用於特定組織 ID、 責任和您指定的繫結屬性的應用程式。 相反地，如果您使用訊息內容屬性，您可以設定 「 泛型 」 的 Wcf-custom 傳送埠，並在訊息層級設定的應用程式內容。  
  
 配接器用戶端必須設定訊息內容屬性傳送至 Oracle E-business Suite，以叫用 Oracle E-business suite 作業的訊息。 中的訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]是不變。 因此，用戶端必須先從現有的訊息，建立一則訊息，然後設定訊息內容屬性的新訊息。 本節中所述的程序，假設現有的訊息稱為**要求**，而新的訊息稱為**New_Request**。  
  
## <a name="set-the-message-context-properties-for-biztalk-applications"></a>設定訊息的 BizTalk 應用程式的內容屬性  
  
1.  開啟 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
2.  在 方案總管 中，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。  
  
3.  在**加入參考**對話方塊中，按一下 **瀏覽**索引標籤，然後再瀏覽至位置其中 BizTalk 屬性結構描述 DLL 的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可用。  
  
     此 DLL， `Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll`，會安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]在\<*安裝磁碟機*>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\bin。  
  
4.  選取 DLL，然後按一下**新增**。  
  
5.  在 BizTalk 協調流程中，新增訊息**New_Request**。 如**訊息類型**屬性，請確定您選取相同的型別做為現有的要求訊息。  
  
6.  「 傳送 」 圖形之前使用的訊息會傳送給傳送埠，加入 「 建構訊息 」 圖形，並在其中，「 訊息指派 」 圖形。  
  
7.  按兩下訊息指派圖形，以開啟**BizTalk 運算式編輯器**。  
  
8.  在**BizTalk 運算式編輯器**，加入下列程式碼，然後按**確定**:  
  
    ```  
    New_Request = Request;  
    New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ApplicationShortName) = "AR";  
    New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ResponsibilityKey) = "RECEIVABLES_VISION_OPERATIONS";  
    New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ResponsibilityName) = "Receivables, Vision Operations (USA)";  
    New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.OrganizationId) = "204";  
    ```  
  
    > [!IMPORTANT]
    >  指定的值**ResponsibilityKey**訊息內容屬性會覆寫指定的值**ResponsibilityName**訊息內容屬性。  
  
9. 請確定進一步處理協調流程的方式是使用**New_Request**訊息。  
  
10. 在部署此協調流程中的前[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須加入組件參考，如`Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll`其中您要部署 「 協調流程的 BizTalk 應用程式中。 若要部署中的組件[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]:  
  
    1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
    2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，，然後您要新增 BizTalk 組件的應用程式。  
  
    3.  以滑鼠右鍵按一下**資源**，指向 **新增**，然後按一下  **BizTalk 組件**。  
  
    4.  在**新增資源**對話方塊中，按一下 **新增**，導覽至包含 BizTalk 組件檔案，這是資料夾\<*安裝磁碟機*>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\bin。 選取`Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll`檔案，然後再按一下**開啟**。  
  
    5.  在**選項**索引標籤上，針對將 BizTalk 組件安裝至全域組件快取 (GAC) 中，指定選項，然後按一下**確定**。  
  
## <a name="set-the-language-for-performing-operations"></a>設定執行作業的語言  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援 Oracle E-business Suite 的多語言支援 (MLS) 功能，並可讓您在執行作業時指定的語言。 配接器會公開**語言**訊息內容屬性來指定執行作業的語言。  
  
 指定的值**語言**訊息內容屬性的值覆寫的**語言**繫結屬性下的**MlsSettings**繫結屬性。 如需有關**MlsSettings**繫結屬性，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
