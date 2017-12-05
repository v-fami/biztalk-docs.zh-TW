---
title: "步驟 11： 測試 AS2 方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 184ed8ee-6778-4bb9-b265-a94a1fed03cb
caps.latest.revision: "34"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cfd7ac057da675f25040685f67301e368605779
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-11-test-the-as2-solution"></a>步驟 11： 測試 AS2 方案
![步驟 11-11](../core/media/tut-step11-of-11.gif "Tut_Step11_of_11")  
  
 在這個步驟中，您將驗證本教學課程的結果。  
  
 您必須建置用來將 EDI 訊息傳送到 Receive_AS2 接收位置的 Sender.exe 檔案 (透過 Contoso 虛擬目錄)。 Sender.exe 會傳回非同步的 MDN 訊息。 訊息檔案為 X12_00401_864.edi，位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial 資料夾中。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-test-the-solution-with-an-asynchronous-edi-message"></a>若要使用非同步 EDI 訊息測試方案  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender 資料夾中的 Sender.csproj 專案。 以滑鼠右鍵按一下 [Sender] 專案，然後按一下**屬性**。 按一下**簽署**左邊的主控台中。 請確認**簽署組件**已選取，並將強式名稱金鑰檔設定為**Sender.snk**。 請確定**延遲簽署只能**已清除。  
  
2.  建置專案。  
  
3.  開啟命令提示字元，並瀏覽至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug。 Enter `Sender.exe`，然後按下**Enter**。 確認您看到一則訊息，指出 AS2 訊息已傳送成功，然後再關閉命令提示字元。  
  
    > [!NOTE]
    >  執行 Sender.exe 組建 AS2 訊息包含下列 EDI 測試交換： [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\X12_00401_864.edi。 建置 AS2 訊息之後，它會將訊息張貼到 Contoso 虛擬目錄，再由此虛擬目錄使用 BTSHttpReceive.dll 將訊息傳送到接收位置。  
  
4.  瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_MDNToFabrikam 資料夾。 請確認有\<GUID\>.msg 資料夾中的檔案。 使用「記事本」開啟檔案，並確認該訊息是 MDN，而且其中的 AS2-From 已設定為 Contoso， AS2-To 則設定為 Fabrikam。  
  
5.  瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_EDIXMLToContoso 資料夾。 請確認有\<GUID\>資料夾中的.xml 檔案。 按兩下檔案，並確認訊息的 ST01 欄位設定為 864。  
  
6.  瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_997ToFabrikam 資料夾。 請確認有\<GUID\>.msg 資料夾中的檔案。 使用「記事本」開啟檔案，並確認訊息是 997 訊息 (ST1 為 997)，而且 EDI 內容上方有 AS2 標頭。 確認 AS2-From 是 Contoso，而 AS2-To 則是 Fabrikam。 確認 ISA6 (傳送者識別項) 設定為 1234567 (Contoso)，而 ISA8 (接收者識別項) 則設定為 7654321 (Fabrikam)。  
  
7.  若要查看 AS2 和 EDI 狀態報告，請移至**群組中樞**在 BizTalk Server 管理主控台頁面上，捲動到頁面底部，按一下其中一個狀態報告連結。 如需詳細資訊，請參閱[EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md)。  
  
## <a name="next-steps"></a>後續步驟  
 您已經完成 AS2 教學課程。  
  
## <a name="see-also"></a>請參閱  
 [教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)   
 [步驟 1：準備 AS2 教學課程](../core/step-1-prepare-for-the-as2-tutorial.md)