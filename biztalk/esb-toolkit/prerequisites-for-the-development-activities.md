---
title: 開發活動的必要條件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 54c91405-f9a4-4676-b5c5-fe90b3b51b45
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbc79fd31e78581d98ecad34579958ff90f3b1e1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006255"
---
# <a name="prerequisites-for-the-development-activities"></a>開發活動的必要條件
本章節描述如何準備您的環境，完成的一部分的開發活動中的步驟[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。 才能嘗試進行任何開發活動中的程序，請完成下列設定：  
  
## <a name="set-up-your-computer-to-perform-the-procedures-in-the-biztalk-esb-toolkit-development-activities"></a>BizTalk ESB Toolkit 開發活動中執行的程序設定您的電腦  
  
1.  安裝和部署路線範例應用程式、 動態解析範例應用程式和多個 Web 服務範例應用程式。 如需有關安裝和部署這些應用程式的詳細資訊，請參閱[BizTalk ESB 工具組範例應用程式](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md)。  
  
2.  執行 「 UDDI 發行者 」 公用程式。  
  
3.  在開發電腦，在 Windows 檔案總管 中，建立下列路徑：  
  
    -   C:\HowTos  
  
    -   C:\HowTos\Itineraries  
  
    -   C:\HowTos\DropFolder  
  
    -   C:\HowTos\Out  
  
4.  請確認您的 BizTalk Server 服務帳戶具有**完全控制**C:\HowTos 目錄結構的權限。  
  
5.  請確認您的 Microsoft BizTalk Server 服務帳戶具有**寫入**C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out 的權限。  
  
6.  複製下列測試訊息到 C:\HowTos 資料夾：  
  
    -   C:\Projects\Microsoft.Practices.ESB\Source\Samples\Itinerary\Test\Data\NAOrderDoc.xml  
  
7.  在 C:\HowTos 資料夾中建立的捷徑至路線測試用戶端應用程式，在下列位置找到：  
  
    -   C:\Projects\Microsoft.Practices.ESB\Source\Samples\Itinerary\Source\ESB。Itinerary.Test\bin\Debug\ESB。Itinerary.Test.exe  
  
## <a name="create-the-visual-studio-solution"></a>建立 Visual Studio 方案  
  
1.  在 Visual Studio 中，在 檔案 功能表上指向**新增**，然後按一下 **專案**。  
  
2.  在**新專案**對話方塊，在 專案類型 窗格中，按一下**Visual C#**，然後按一下 **類別庫**在範本窗格中。  
  
3.  在**名稱**方塊中，輸入**ItineraryLibrary**。  
  
4.  在**位置**方塊中，輸入**C:\HowTos**。  
  
5.  選取**為方案建立目錄**核取方塊。  
  
6.  在**方案名稱**方塊中，輸入**模式**，然後按一下**確定**即可建立方案。  
  
7.  刪除**Class1.cs**檔案從**ItineraryLibrary**專案。