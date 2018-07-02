---
title: 步驟 1： 準備 EDI 介面開發人員教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9be1bddf-d673-4054-87f5-0205b8b5cc0d
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0823f42f5f7963d1c70f1b2d7e16ed595d01bd83
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972975"
---
# <a name="step-1-prepare-for-the-edi-interface-developer-tutorial"></a>步驟 1： 準備 EDI 介面開發人員教學課程
![步驟 1 的 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-1of9.gif "Step_1of9")  
  
 EDI 介面開發人員教學課程是在單一電腦上執行。 若要準備本教學課程，您必須安裝和設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中所述[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)。 您也必須新增 BizTalk EDI 應用程式的參考。  
  
> [!NOTE]
>  本教學課程中運作，它必須使用 IIS 7.5 或 IIS 8 的平台上將其執行。  
  
 EDI 介面開發人員教學課程所需檔案位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial 資料夾中。 教學課程所需的資料夾和檔案如下：  
  
|資料夾\檔案|目的|  
|------------------|-------------|  
|\SDK\EDI Interface Developer Tutorial\EDI Inbound Processing.sln|您在 Visual Studio 用來建立此傳訊實例的解決方案檔案|  
|\SDK\EDI Interface Developer Tutorial\keyfile.snk|解決方案檔案指定的組件金鑰檔案|  
|\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\SamplePO.txt|您用來測試解決方案的範例訊息檔案 (4010 850 版)|  
|\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\Inbound4010850_to_OrderFile.btm|將 850 訊息資料轉換為「訂單系統」所需格式的 BizTalk 對應。|  
|\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\SendOrderFilePipeline.btp|處理測試訊息的傳送管線，可將訊息傳送至訂單系統。|  
|\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\X12_00401_850.xsd|測試訊息的 850 結構描述。|  
\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\fromTHEM|存放從 Fabrikam 接收而來之輸入 850 訊息的資料夾|  
|\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\toOrderSystem|輸出 850 訊息的傳送目標資料夾，代表您的「訂單系統」後端應用程式|  
|\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\toTHEM_997|997 通知的傳送目標資料夾，代表 Fabrikam|  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-add-reference-to-the-biztalk-edi-application"></a>若要加入 BizTalk EDI 應用程式的參考  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，底下**應用程式**] 節點，以滑鼠右鍵按一下您想要使用 edi，例如 [BizTalk Application 1 的應用程式。 指向**新增**，然後按一下 參考。  
  
2. 在 **新增應用程式參考**對話方塊中，選取**BizTalk EDI 應用程式**，然後按一下**確定**。  
  
## <a name="next-steps"></a>後續步驟  
 建置和部署 Inbound_EDI 組件中所述[步驟 2： 更新和部署教學課程解決方案](../core/step-2-update-and-deploy-the-tutorial-solution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 2: EDI 介面開發人員教學課程](../core/tutorial-2-edi-interface-developer-tutorial.md)