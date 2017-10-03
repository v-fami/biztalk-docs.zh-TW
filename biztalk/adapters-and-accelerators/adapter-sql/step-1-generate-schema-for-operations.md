---
title: "步驟 1： 作業產生結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63218a5e-9af2-40af-9992-ac5e204d2832
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16372bd950088b89f8e7808cda751f5fc3833944
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-generate-schema-for-operations"></a>步驟 1： 作業產生結構描述
![步驟 2 之 1](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：**在此步驟中，您會產生結構描述在 SQL Server 資料庫使用中執行的作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 此教學課程中，您必須產生以下的結構描述：  
  
-   **通知**（輸入作業）。  
  
-   **UPDATE_EMPLOYEE**預存程序 （輸出作業）。  
  
-   **插入**作業**Purchase_Order**資料表 （輸出作業）。  
  
## <a name="prerequisites"></a>必要條件  
 在繼續本教學課程之前，請確定：  
  
-   您必須先完成中的步驟[之前您開發 BizTalk 應用程式](http://msdn.microsoft.com/library/3539741d-5266-43d4-9b7b-73e82f0ed4f6)。  
  
-   您必須以 BizTalk Server 系統管理員群組的成員登入。  
  
### <a name="to-generate-schema-for-operations"></a>若要產生結構描述的作業  
  
1.  建立新的 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 此教學課程中，做為專案名稱， `Employee_PurchaseOrder`。  
  
2.  ADAPTER_SAMPLES SQL Server 資料庫使用以連接到[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 如需如何使用連接的指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請參閱[連接到 Visual Studio 使用取用配接器服務增益集中的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)。  
  
    > [!NOTE]
    >  您也可以連接到 SQL Server 使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 不過，本教學課程中您會使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
3.  產生結構描述的**通知**輸入作業。  
  
    1.  在連接到 ADAPTER_SAMPLES 資料庫之後, [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，從**選取合約型別**清單中，選取**服務 （輸入操作）**。  
  
    2.  從**選取類別目錄**方塊中，按一下根節點 (**/**)。  
  
    3.  從**可用的類別和作業**方塊中，選取**通知**按一下**新增**。 **通知**作業現在會顯示在**加入的類別和作業**方塊。 按一下 **[確定]**。  
  
4.  產生結構描述的**UPDATE_EMPLOYEE**上預存程序和插入作業**Purchase_Order**資料表。  
  
    1.  重複步驟 2，連接到 SQL Server 使用 ADAPTER_SAMPLES 資料庫[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
        > [!NOTE]
        >  您無法在相同的時間來產生結構描述的輸入和輸出作業。 因此，在步驟 3，在您按一下之後**確定**產生結構描述**通知**作業，[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]關閉。 您必須重新連接到 SQL Server 資料庫來產生結構描述的傳出作業。  
  
    2.  從**選取合約型別**清單中，選取**用戶端 （輸出作業）**。  
  
    3.  從**選取類別目錄**方塊中，按一下**Strongly-Typed 程序**節點。 從**可用的類別和作業**s 方塊中，選取**UPDATE_EMPLOYEE**，然後按一下 **新增**。  
  
        > [!IMPORTANT]
        >  **UPDATE_EMPLOYEE**預存程序也會提供下**程序**節點。 不過，如果您產生結構描述的預存程序從**程序**節點，回應訊息結構描述無法在設計階段，但是之後執行預存程序可能會收到回應訊息。  
        >   
        >  在此教學課程中，您將對應的插入作業的輸入結構描述的預存程序的回應結構描述上**Purchase_Order**資料表。 因此，您將需要的結構描述**UPDATE_EMPLOYEE**預存程序，在設計階段和您必須選取預存程序從**Strongly-Typed 程序**。 如此一來，您會在設計階段收到預存程序的結構描述。  
  
    4.  從**選取類別目錄**方塊中，展開 **資料表**節點中，按一下節點**Purchase_Order**資料表。 從**可用的類別和作業**s 方塊中，選取**插入**，按一下 **新增**，然後按一下 **確定**。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您會產生結構描述**通知**（輸入作業） **UPDATE_EMPLOYEE**預存程序，和**插入**作業**Purchase_Order**資料表。 在您產生結構描述中之後,[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]將下列檔案加入至您的 BizTalk 專案：  
  
-   包含要叫用 SQL Server 上的作業的要求訊息的結構描述的 XSD 檔案。  
  
-   可用來建立 Wcf-custom 傳送埠和接收埠中的 XML 繫結檔案[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
 如需有關如何產生結構描述的詳細資訊，請參閱[瀏覽、 搜尋和使用 SQL 配接器的 SQL 作業的 get 中繼資料](../../adapters-and-accelerators/adapter-sql/browse-search-and-get-metadata-for-sql-operations-using-the-sql-adapter.md)。  
  
## <a name="next-steps"></a>後續步驟  
 您可以建立訊息中的結構描述的 BizTalk 專案中[步驟 2： 建立訊息的 BizTalk 協調流程](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [第 1 課： 產生結構描述和建立訊息](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)