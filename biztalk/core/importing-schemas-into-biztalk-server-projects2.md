---
title: "結構描述匯入到 BizTalk Server Projects2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing schemas
- schemas, importing into BizTalk Server projects
ms.assetid: 640d5884-953a-46b6-b9dc-b931392a3059
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ebb0a39850029adec06986da5ddad1fc44c33ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-schemas-into-biztalk-server-projects"></a>結構描述匯入至 BizTalk Server 專案
本節討論瀏覽 JD Edwards EnterpriseOne 伺服器，以及將結構描述匯入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案。  
  
> [!NOTE]
>  您必須確定您已設定引數清單。 在協調流程中產生結構描述之前，您必須先更新 jdearglist.txt。 如需詳細資訊，請參閱[處理字串值](../core/handling-string-values2.md)。  
  
> [!NOTE]
>  每次變更 jdearglist 時，都必須為該商務物件重新產生結構描述。  
  
 在建立 JD Edwards EnterpriseOne 連接埠後，您可以從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案啟動 Microsoft 配接器精靈，以瀏覽 JD Edwards EnterpriseOne。  
  
### <a name="to-import-schemas-into-a-biztalk-server-project"></a>將結構描述匯入 BizTalk Server 專案  
  
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
  
### <a name="to-select-the-schemas"></a>選取結構描述  
  
1.  在**選取要匯入服務**頁面上，展開最上層節點**商務物件**節點或**商務服務**節點。  
  
2.  選取您想要匯入，然後按一下的項目旁的核取方塊**確定**。  
  
3.  針對所選 JD Edwards EnterpriseOne 項目產生的結構描述就會匯入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案。  
  
> [!NOTE]
>  使用 AddressBook (N0100041) 時，欄位名稱為**cActionCode**。 動作是 XML 檔案本身的一部分。 程式碼為：  
  
-   A 表示新增  
  
-   C 表示變更  
  
-   D 表示刪除  
  
-   I 表示查詢  
  
## <a name="see-also"></a>另請參閱  
 [建立 JD Edwards EnterpriseOne 傳送處理常式](../core/creating-jd-edwards-enterpriseone-send-handlers.md)