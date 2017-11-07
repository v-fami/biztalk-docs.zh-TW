---
title: "JD Edwards EnterpriseOne 結構描述匯入 Visual Studio |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 640d5884-953a-46b6-b9dc-b931392a3059
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acd61cc8ab63d6859a8e10afb76f93c2f8cb2150
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="importing-schemas-into-biztalk-server-projects"></a>結構描述匯入至 BizTalk Server 專案
本節討論瀏覽 JD Edwards EnterpriseOne 伺服器，以及將結構描述匯入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案。  
  
> [!NOTE]
>  您必須確定您已設定引數清單。 在協調流程中產生結構描述之前，您必須先更新 jdearglist.txt。 如需詳細資訊，請參閱[處理字串值](../core/handling-string-values2.md)。  
  
> [!NOTE]
>  每次變更 jdearglist 時，都必須為該商務物件重新產生結構描述。  
  
 在建立 JD Edwards EnterpriseOne 連接埠後，您可以從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案啟動 Microsoft 配接器精靈，以瀏覽 JD Edwards EnterpriseOne。  
  
## <a name="import-schemas-into-visual-studio"></a>結構描述匯入 Visual Studio
  
1.  開啟 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
2.  以滑鼠右鍵按一下名稱[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案，指向**新增**，然後選取**新增產生的項目**。  
  
3.  按一下**新增**開啟**新增配接器精靈**。  
  
4.  在**選取配接器**頁面上，選取您要匯入結構描述的配接器名稱 (例如， **JDEEnterpriseOne**)。  
  
5.  在**SQL Server**方塊中，選取 SQL server。  
  
6.  在**資料庫**方塊中，選取資料庫。  
  
     預設的資料庫和 SQL Server 的相同。  
  
7.  在**連接埠**，選取 SQL server，然後按一下 **下一步**。  
  
     JD Edwards EnterpriseOne 系統就會顯示在瀏覽器中。  
  
8.  繼續下一個程序。  
  
 「新增配接器精靈」會顯示含有所有已定義系統的樹狀結構。 JD Edwards EnterpriseOne 有許多模組。 模組會依據名稱中的前三個字元分組。  
  
-   階層的第一層是模組名稱所有三個字元的首碼清單。  
  
-   第二層列示共用相同的三個字元首碼的所有模組。  
  
-   最後一層列示屬於模組的商務功能。 當您展開服務圖示時，就能檢視它的作業。  
  
 展開作業會顯示輸入/輸出引數。 您可以展開輸入/輸出引數以檢視引數的資料類型。  
  
> [!NOTE]
>  如果伺服器物件定義變更，您必須重新產生結構描述以重新整理其中包含的資料。  
  
> [!NOTE]
>  如果您在產生結構描述後變更 jdearglist.txt，您必須重新產生結構描述以重新整理所包含的資料。 如需 jdearglist.txt 的相關詳細資訊，請參閱[處理字串值](../core/handling-string-values2.md)。  
  
## <a name="select-the-schemas"></a>選取的結構描述  
  
1.  在**選取要匯入服務**頁面上，展開最上層節點**商務物件**節點或**商務服務**節點。  
  
2.  選取您想要匯入，然後按一下的項目旁的核取方塊**確定**。  
  
3.  針對所選 JD Edwards EnterpriseOne 項目產生的結構描述就會匯入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案。  
  
> [!NOTE]
>  使用 AddressBook (N0100041) 時，欄位名稱為**cActionCode**。 動作是 XML 檔案本身的一部分。 程式碼為：  
  
-   A 表示新增  
  
-   C 表示變更  
  
-   D 表示刪除  
  
-   I 表示查詢  
  
## <a name="next-step"></a>下一步
[使用訊息內容屬性](../core/using-message-context-properties1.md)