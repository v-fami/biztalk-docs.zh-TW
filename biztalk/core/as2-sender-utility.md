---
title: AS2 傳送者公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e2a88fc-67fd-4801-a6f8-1e7c92098eaf
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2b07b2d791f4870b608e552189cd2f35754c950
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998215"
---
# <a name="as2-sender-utility"></a>AS2 傳送者公用程式
隨附於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 AS2 傳送者公用程式可讓您將 AS2 訊息傳送到單一電腦上的網站。 這個公用程式可模擬從個別電腦傳送 AS2 訊息的動作。  
  
 AS2 傳送者公用程式檔案位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender 中。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
## <a name="what-this-utility-does"></a>這個公用程式的作用  
 AS2 傳送者公用程式會使用 EDI 內容建置 AS2 訊息，並將該訊息傳送到使用 BTSHTTPReceive ISAPI 篩選器的網站。 根據預設，教學課程執行的作業包括：  
  
- 傳送名為 X12_00401_864.edi 且具有 864 X12 編碼內容的 AS2 訊息。 此訊息位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial 資料夾內。  
  
- 提示非同步 MDN 以回應 AS2 訊息。 這是由傳送的訊息決定，而且可以變更。  
  
- 透過 Contoso 虛擬目錄將 AS2 訊息傳送至接收位置。  
  
  您可以修改公用程式來變更這種特定行為。 請參閱[如何自訂 AS2 傳送者公用程式](../core/as2-sender-utility.md#BKMK_Custom)下一節。  
  
## <a name="how-to-set-up-a-solution-using-the-as2-sender-utility"></a>如何設定使用 A2 傳送者公用程式的方案  
 若要將方案設定成使用 AS2 傳送者公用程式，您必須執行下列步驟：  
  
> [!IMPORTANT]
>  AS2 教學課程與兩個 AS2 傳送端逐步解說中都示範了這些步驟。 如需詳細資訊，請參閱 <<c0> [ 教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)，[逐步解說 (AS2): 使用同步 MDN 透過 AS2 傳送的 EDI](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md)，和[逐步解說 (AS2): 使用非同步透過 AS2 傳送的 EDIMDN](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md)。  
  
-   啟用 BTSHTTPReceive ISAPI 篩選器。  
  
-   設定用來接收 AS2 訊息的網頁和接收位置。 在預設的 AS2 傳送者公用程式中，此網頁為 Contoso 網頁。  
  
-   部署您要傳送成 AS2 訊息內容之 EDI 交換的結構描述。  
  
-   設定適當的 AS2 和 EDI 合作對象屬性。  
  
##  <a name="BKMK_Custom"></a> 如何自訂 AS2 傳送者公用程式  
 預設的 AS2 傳送者公用程式會透過 AS2 將測試 864 EDI 交換傳送到使用 BTSHTTPReceive ISAPI 篩選器的 Contoso 網頁。 AS2 訊息 (名稱為 X12_00401_864.edi) 會提示非同步的 MDN。 AS2 傳送者公用程式程式碼位於內的 HttpSender.cs 中[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]AS2 Tutorial\Sender 資料夾。 HttpSender.cs 中的下面這行程式碼會傳送預設的 864 測試檔案：  
  
```  
Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864.edi", FileMode.Open, FileAccess.Read);  
```  
  
> [!NOTE]
>  您可以使用不同的檔案名稱和不同的路徑來修改這行程式碼。  
  
 HttpSender.cs 中的下列一行會傳送名為 X12_00401_864-Sync.edi 的 AS2 訊息。 這個訊息會提示同步的 MDN。 根據預設，HttpSender.cs 中這一行程式碼已標記為註解，改由傳送 X12_00401_864.edi 的程式碼代替。 若要傳送 X12_00401_864-Sync.edi，請移除 X12_00401_864-Sync.edi 一行的註解標記，並將 X12_00401_864.edi 一行標記為註解。  
  
```  
Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864-Sync.edi", FileMode.Open, FileAccess.Read);  
```  
  
 HttpSender.cs 中的下面這行程式碼會將訊息傳送至 Contoso 網頁：  
  
```  
HttpSender TestSender = new HttpSender("http://localhost/Contoso/BTSHttpReceive.dll");  
```  
  
> [!NOTE]
>  您可以使用不同的虛擬目錄和 ISAPI 篩選器來修改這行程式碼。  
  
### <a name="to-build-the-as2-sender-sample"></a>若要建置 AS2 傳送者範例  
  
1. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender 資料夾中的 Sender.csproj 專案。  
  
2. 開啟 Sender 專案中的 HttpSender.cs，並使用適當的網頁和適當的 EDI 檔案名稱和路徑自訂傳送者程式碼。  
  
3. Sender 專案中，以滑鼠右鍵按一下，然後按一下 **屬性**。  
  
4. 按一下 **簽署**左邊的主控台中。 請確認**簽署組件**已選取，且強式名稱金鑰檔設為**Sender.snk**。 請確定**僅延遲簽署**已清除。  
  
5. 建置專案。  
  
### <a name="to-run-the-as2-sender-sample"></a>若要執行 AS2 傳送者範例  
  
1. 開啟命令提示字元。 移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug。  
  
2. Enter **Sender.exe**，然後按**Enter**。  
  
3. 確認您看到一則訊息，指出 AS2 訊息已傳送成功，然後再關閉命令提示字元。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)   
 [逐步解說 (AS2): 使用同步 MDN 透過 AS2 傳送 EDI](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md)   
 [逐步解說 (AS2)：使用非同步 MDN 透過 AS2 傳送 EDI](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md)