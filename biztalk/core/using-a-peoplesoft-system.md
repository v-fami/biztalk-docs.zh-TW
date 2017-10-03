---
title: "使用 PeopleSoft 系統 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c228ac23-184f-4c08-922b-ba84f5f2c52f
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c93e025ddb2ccec4b0088c20837a4f307f40aada
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-peoplesoft-system"></a>使用 PeopleSoft 系統
您可以從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統使用 PeopleSoft 配接器存取 PeopleSoft 系統。 此配接器是一群八個 Microsoft 隨附以供搭配使用的特定業務 (LOB) 配接器的其中一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
 PeopleSoft 實驗室工作分成兩個部分。 第一個實驗室 (實驗室 1) 可讓您不需要使用 PeopleSoft 系統[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或任何 Microsoft 產品 （但可能是 Internet Explorer 中，但是您可以使用任何瀏覽器）。 在這個實驗室中，您將會連接至 PeopleSoft 系統來找出和修改的簡單資料記錄。  
  
 在第二個實驗室 (實驗室 2) 中，您將建立 BizTalk 專案和協調流程。 建立應用程式之後，您會將它部署，並使用它來連線至 PeopleSoft 系統使用 PeopleSoft 配接器。 目標是透過 BizTalk 應用程式存取資料，使用配接器。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本實驗室的程序，您需要在瀏覽器和網際網路連線，以及 PeopleSoft 系統上的使用者帳戶。 您需要知道要瀏覽至您的 PeopleSoft 系統的 Web 存取的位置。 您不需要[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或任何其他 Microsoft 技術。  
  
## <a name="lab-1---using-a-peoplesoft-system"></a>實驗室 1-使用 PeopleSoft 系統  
 在這個實驗室中，您將使用 PeopleSoft 系統，而不使用的任何元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 目標是要測試您的連線以確保能夠正確地設定第二個實驗室 PeopleSoft。 一開始您連接至 PeopleSoft 系統透過 Web 介面，可讓您使用如 Internet Explorer 的瀏覽器登入。  
  
## <a name="procedures-for-lab-1---using-a-peoplesoft-system"></a>實驗室 1-使用 PeopleSoft 系統的程序  
  
#### <a name="to-log-on-to-peoplesoft-by-using-a-browser"></a>使用瀏覽器登入 PeopleSoft  
  
-   瀏覽 PeopleSoft 登入網頁登入 PeopleSoft 系統。 輸入您**使用者識別碼**和**密碼**，然後按一下 **登入**。  
  
     ![](../core/media/1e3e5c0f-316b-4aa3-946e-3bb3665b0ddb.gif "1e3e5c0f-316b-4aa3-946e-3bb3665b0ddb")  
  
#### <a name="to-locate-and-modify-peoplesoft-data"></a>若要找出和修改 PeopleSoft 資料  
  
1.  成功的登入將放在您個人化您選擇其配置看到的內容頁面。 向下捲動並展開**設定財務/供應鏈**，按一下 **一般定義**，按一下 **位置**，然後按一下 **位置**一次。 這會帶您到**位置**搜尋介面。  
  
     ![](../core/media/62a89cd4-464c-42fd-91cd-60ceeab5b006.gif "62a89cd4-464c-42fd-91cd-60ceeab5b006")  
  
2.  若要開始搜尋，請設定**SetID**至 **=** ，將**Location Code**至**開頭**，輸入，然後按一下 **搜尋**。 這會顯示其名稱開頭中的城市**搜尋結果**介面區段。  
  
     ![](../core/media/86661144-c666-4d72-9227-9f17df715ba4.gif "86661144-c666-4d72-9227-9f17df715ba4")  
  
3.  按一下其中一個位置，以取得詳細資訊。 例如，在下圖中，使用者按一下**AUS01**中連結**Location Code**資料行。  
  
4.  輸入其中一個欄位的一些新的資料 (例如**位址 2**欄位)，按一下 **儲存**左下角。 這會將新輸入的資料儲存到記錄中。  
  
     ![](../core/media/b6eb137c-c0b0-4906-8fbd-1bc036069fb0.gif "b6eb137c-c0b0-4906-8fbd-1bc036069fb0")  
  
5.  若要確認這項變更成功，重複步驟 2 中的程序、 尋找此相同的記錄一次，並觀察記錄所做的變更。  
  
6.  在視窗右上方部分中，按一下**登出**結束您的 PeopleSoft 工作階段。  
  
     ![](../core/media/7760b541-5155-453e-a682-4780412f3c13.gif "7760b541-5155-453e-a682-4780412f3c13")  
  
    > [!NOTE]
    >  在下一個實驗室中有使用 PeopleSoft 配接器擷取您所修改的位置記錄 (AUS01) 資訊的指示。  
  
## <a name="summary"></a>摘要  
 在這個實驗室中您可登入 PeopleSoft 系統，透過瀏覽器。 您已連接之後，您搜尋的資料，然後操作並更新資料錄的地址欄位。 後認可變更，您無法修改的資料瀏覽器中檢視可讓您確認變更正確執行。