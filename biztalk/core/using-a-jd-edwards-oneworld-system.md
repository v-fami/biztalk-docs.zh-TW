---
title: 使用 JD Edwards OneWorld 系統 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5346aa04-ebd7-4545-9062-b349fd73b7f1
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 835432e50bce3f347e6f769fb8182ab35fc4f949
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287470"
---
# <a name="using-a-jd-edwards-oneworld-system"></a>使用 JD Edwards OneWorld 系統
您可以使用 JD Edwards OneWorld 配接器從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統存取 JD Edwards OneWorld 系統。 此配接器是一群八個 Microsoft 隨附以供搭配使用的特定業務 (LOB) 配接器的其中一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
 JD Edwards OneWorld 實驗室的工作分成兩個部分。 第一個實驗室 (實驗室 1) 讓您不需有 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 或任何 Microsoft 產品，即可使用 JD Edwards OneWorld 系統。 您將會使用 JD Edwards OneWorld Client 工具連接至 JD Edwards OneWorld 資料庫，並且根據位址找出特定記錄。  
  
 在第二個實驗室 (實驗室 2) 中，您將建立 BizTalk 專案和協調流程。 建立應用程式之後，您將會使用 JD Edwards OneWorld 配接器來部署它並使用它來連線至 JD Edwards OneWorld 系統。 目標是透過 BizTalk 應用程式存取資料，使用配接器。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此實驗室的程序，您需要安裝 JD Edwards OneWorld 用戶端軟體及其最新更新。 若要使用任何用戶端軟體工具，您需要有 JD Edwards OneWorld 資料庫、與該資料庫的網路連線，以及該系統上的使用者帳戶。 您不需要有 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 即可完成此實驗室。  
  
## <a name="lab-1---using-a-jd-edwards-oneworld-system"></a>實驗室 1 - 使用 JD Edwards OneWorld 系統  
 在此實驗室中，您將會在不使用任何 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 元件的情況下，使用 JD Edwards OneWorld 系統。 目標是要測試您對 JD Edwards OneWorld 的連線能力，以確定第二個實驗室可正常進行。 您將會使用 JD Edwards OneWorld SQL Plus 工具建立和操作 JD Edwards OneWorld 資料庫中的資料表。  
  
## <a name="procedures-for-lab-1---using-a-jd-edwards-oneworld-system"></a>實驗室 1 - 使用 JD Edwards OneWorld 系統的程序  
  
#### <a name="to-log-on-to-jd-edwards-oneworld-by-using-a-browser"></a>使用瀏覽器登入 JD Edwards OneWorld  
  
-   JD Edwards OneWorld 圖示，即可登入 JD Edwards OneWorld 系統。 輸入您**使用者識別碼**，**密碼**，和**環境**，然後按一下 **確定**。  
  
     ![](../core/media/f04db2ef-d587-4357-b9e8-c96319886e97.gif "f04db2ef-d587-4357-b9e8-c96319886e97")  
  
#### <a name="to-locate-and-view-jd-edwards-oneworld-data"></a>若要找出並檢視 JD Edwards OneWorld 資料  
  
1.  成功的登入將放在您**JD Edwards OneWorld 總管**。  
  
     ![](../core/media/14e8c206-7e38-48f8-9108-e32a7ac9a740.gif "14e8c206-7e38-48f8-9108-e32a7ac9a740")  
  
2.  展開**主目錄**，然後**基礎系統**，然後**通訊錄**，然後**每日處理**。  
  
     ![](../core/media/1f742221-00e5-4697-95ff-64aa63ed567a.gif "1f742221-00e5-4697-95ff-64aa63ed567a")  
  
3.  在右視窗中，按兩下**通訊錄修訂**。  
  
     ![](../core/media/a6d4e871-9c9c-4bc0-9c4f-4bdfd7cc5031.gif "a6d4e871-9c9c-4bc0-9c4f-4bdfd7cc5031")  
  
4.  如**Alpha 名稱**，輸入`Ga`，選取**顯示位址**核取方塊，然後**尋找**工具列上。  
  
     ![](../core/media/2f58413f-41a9-4ed9-ba5c-1d6d59eafb01.gif "2f58413f-41a9-4ed9-ba5c-1d6d59eafb01")  
  
     在**通訊錄修訂-[使用位址]** 對話方塊中，做為搜尋結果不會顯示兩個記錄。  
  
     ![](../core/media/9284df4e-ca9b-48ab-b2bf-a90d765d4a05.gif "9284df4e-ca9b-48ab-b2bf-a90d765d4a05")  
  
     尋找資料的替代方法是清除**Alpha 名稱**欄位中，按一下上面的文字方塊中的 **位址編號**資料行，並輸入`500`。 按一下**尋找**顯示搜尋結果 工具列上。  
  
     ![](../core/media/a88bd867-9a16-416a-a43e-cdfcc65fc670.gif "a88bd867-9a16-416a-a43e-cdfcc65fc670")  
  
     在實驗室 2 中，會使用 JD Edwards OneWorld 配接器擷取的資訊的指示**位址編號**的`500`。  
  
5.  在**檔案**功能表上，按一下 **結束**結束 JE Edwards OneWorld 用戶端工作階段。  
  
## <a name="summary"></a>摘要  
 在此實驗室中，您使用了 JD Edwards OneWorld Client 工具登入 JD Edwards OneWorld 系統。 您已連接之後，您會搜尋特定的資料，而檢視傳回的資料記錄。