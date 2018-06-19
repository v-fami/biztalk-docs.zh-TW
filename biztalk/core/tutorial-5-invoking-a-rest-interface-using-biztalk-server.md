---
title: 教學課程 5： 叫用 REST 介面使用 BizTalk Server |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73871ca3-abd0-45ae-b379-6df76a967a80
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fce915ec277b1f73f93a9508a5dd6c92fb0a5c9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287294"
---
# <a name="tutorial-5-invoking-a-rest-interface-using-biztalk-server"></a>教學課程 5： 叫用 REST 介面使用 BizTalk Server
此章節提供如何叫用 REST 端點使用的逐步解說[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 在本教學課程叫用 REST 端點可從[!INCLUDE[winazure](../includes/winazure-md.md)]Marketplace 傳回延遲班機美式空中承運業者寄送。 本教學課程會使用新**Wcf-webhttp**配接器中導入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]叫用 REST 端點。  
  
##  <a name="BKMK_Scenario"></a>在本教學課程案例  
 [!INCLUDE[winazure](../includes/winazure-md.md)]Marketplace 提供下列 REST 資源 URL，以擷取航班延誤的美國空中電信業者：  
  
```  
https://api.datamarket.azure.com/oakleaf/US_Air_Carrier_Flight_Delays_Incr/On_Time_Performance  
```  
  
 如果您在網頁瀏覽器的網址列輸入此 URL，系統會提示您認證以存取資源。 您登入之後[Windows Azure Marketplace](http://go.microsoft.com/fwlink/p/?LinkId=257913)，您可以取得的認證從**我的帳戶**web 頁面的索引標籤。 認證會列出針對**客戶 ID** （使用者名稱） 和**主要帳戶金鑰**（密碼） 標籤。  
  
 在本教學課程中，您使用的資源 URL 和認證來設定雙向**Wcf-webhttp**傳送埠。 接收管線的雙向傳送埠接收回應訊息與飛行詳細資料，並將發佈的訊息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]messagebox 資料庫。 您設定訂閱 Wcf-webhttp 傳送埠所發行的所有訊息的 FILE 傳送埠。 FILE 傳送埠取用訊息從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]並將它複製到檔案位置。  
  
 在真實世界的商業案例中，將它與較大的商務程序，例如商務應用程式從取得訊息的接收位置關聯可以觸發 Wcf-webhttp 傳送埠。 不過，在本教學課程中，因為的重點在於示範如何叫用 REST 介面，您可以使用簡單的檔案位置接收到觸發程序的傳送埠將虛擬訊息。  
  
 因此，簡單來說，您必須執行下列步驟來設定此解決方案：  
  
1.  設定檔案接收位置挑選虛擬要求訊息。  
  
2.  設定雙向 Wcf-webhttp 傳送埠以叫用 REST 資源 URL，並接收回應。  
  
3.  設定單向 FILE 傳送埠取用回應訊息的飛行詳細資料，並將它複製到檔案位置。  
  
## <a name="set-up-your-includewinazureincludeswinazure-mdmd-marketplace-account"></a>設定您[!INCLUDE[winazure](../includes/winazure-md.md)]的 Marketplace 帳戶  
 若要存取 公開透過 REST 端點的飛行延遲資料，您必須先訂閱美國空中載波航班延誤範例資料摘要。 執行下列步驟來執行這項操作：  
  
#### <a name="to-subscribe-to-the-data-feed"></a>若要訂閱的資料摘要  
  
1.  登入[!INCLUDE[winazure](../includes/winazure-md.md)]Marketplace 使用您的 Microsoft 帳戶。  
  
2.  在**資料**索引標籤上，找出並按一下**美國空中載波航班延誤**服務。  
  
3.  在 [資料服務] 頁面上按一下**註冊**。 在登入頁面上，接受合約的條款，然後按一下 **註冊**一次。  
  
4.  在**我的帳戶**索引標籤上，擷取來存取資料服務的認證。 認證會列出針對**客戶 ID** （使用者名稱） 和**主要帳戶金鑰**（密碼） 標籤。 設定時，您會需要這些認證**Wcf-webhttp**傳送埠。  
  
## <a name="set-up-your-computer"></a>設定電腦  
 若要設定在本教學課程，您必須使用的案例[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您的電腦上安裝和設定。 如果您想要佈建[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦上 Windows Azure VM，請遵循指示[Azure VM 上設定 BizTalk Server](http://msdn.microsoft.com/library/azure/jj248689.aspx)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1： 設定檔案接收位置](../core/step-1-configure-a-file-receive-location.md)  
  
-   [步驟 2： 設定雙向 Wcf-webhttp 傳送埠](../core/step-2-configure-a-two-way-wcf-webhttp-send-port.md)  
  
-   [步驟 3： 設定單向 FILE 傳送埠](../core/step-3-configure-a-one-way-file-send-port.md)  
  
-   [步驟 4： 測試方案](../core/step-4-test-the-solution.md)