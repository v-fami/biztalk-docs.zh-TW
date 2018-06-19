---
title: 執行單元測試 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 40275d0b-b2ee-400c-9ef5-b9386ab0ae53
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a2084e2e46e3e984af2c5466c52862956dc8414
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009855"
---
# <a name="performing-unit-testing"></a>執行單元測試
單元測試會著重在元件層級和基本上是通過/失敗測試，以確認如預期般，是否要執行的 BizTalk 方案的個別元件。 您有針對單元測試您的 BizTalk 方案的數個選項。  
  
## <a name="using-visual-studio"></a>使用 Visual Studio  
 單元測試功能是適用於 Visual Studio 2008 和更新版本。 如需適用於 Visual Studio 的測試功能的詳細資訊，請參閱[測試應用程式](http://go.microsoft.com/fwlink/?LinkId=159595)(http://go.microsoft.com/fwlink/?LinkId=159595)。  
  
 BizTalk Server 也提供了單元測試功能，讓使用者可以建立結構描述、 對應和管線的單元測試。 如需有關這項功能的詳細資訊，請參閱[單元測試使用 BizTalk Server 專案](http://go.microsoft.com/fwlink/?LinkId=158270)(http://go.microsoft.com/fwlink/?LinkId=158270)。  
  
> [!NOTE]  
>  Visual Studio 是非常適用於單元測試 BizTalk 成品，例如協調流程、 結構描述、 管線和管線元件。 BizTalk Server 提供測試類別，您可以搭配 Visual Studio Team System 測試 BizTalk 成品。  
  
## <a name="using-non-microsoft-tools"></a>使用非 Microsoft 工具  
 單元測試 BizTalk 解決方案的其他兩個常用的工具是**BizUnit**和**NUnit**。 **BizUnit**順暢地搭配 Visual Studio Team System Test 版。 同樣地， **NUnit**測試可以輕鬆地修改，讓它們可以做為執行-在 Visual Studio Team System Test 版。 如需有關這些工具的詳細資訊，請參閱[工具測試](~/technical-guides/tools-for-testing.md)。  
  
> [!NOTE]  
>  使用**BizUnit**和**NUnit**不會受到 Microsoft，Microsoft 並不保證這些程式的適用性。 請自行承擔使用這些程式的一切風險。  
  
## <a name="using-the-biztalk-server-sdk"></a>使用 BizTalk Server SDK  
 您可以執行單元測試之個別的 BizTalk 成品的公用程式中可用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SDK。 下表提供可以用於單元測試的 SDK 中的公用程式的摘要：  
  
|**公用程式**|**目的**|  
|-----------------|-----------------|  
|AS2 傳送者公用程式|可讓您在單一電腦上的網站傳送 AS2 訊息。 這個公用程式可模擬從個別電腦傳送 AS2 訊息的動作。|  
|DSDump.exe|可讓您傾印文件結構描述結構，也就是一或多個 XSD 結構描述在記憶體中的輕量型表示法 (不論是否有一般檔案註解)。 當您發生剖析引擎錯誤 (例如 $Root$0$3$2) 且需要將錯誤解碼時，這個工具就很有用。 $ 後面的數字代表出現在文件結構描述中以 0 為基礎的索引或記錄。|  
|FFAsm.exe|執行一般檔案組合器元件，並透過模擬傳送管線直接叫用該元件，讓您能夠查看它如何將使用者的 XML 文件序列化或組合成一般檔案文件。|  
|FFDasm.exe|執行一般檔案解譯器元件，並透過模擬接收管線直接叫用該元件，讓您能夠查看它如何剖析或是將使用者的一般檔案文件解譯成一或多個 XML 文件。|  
|Pipeline.exe|執行傳送或接收管線。可接受一或多個輸入的文件及其組件、 XSD 結構描述，以及相關的資訊;並產生輸出文件的管線之後執行。 Pipeline.exe 不會存取[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，因此包含存取 BizTalk Framework 組合器和解譯器元件的管線[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可能不支援在執行期間的資料庫。|  
|XMLAsm.exe|執行 XML 組合器元件，並透過模擬傳送管線直接叫用該元件，讓您能夠查看它如何將使用者的 XML 文件序列化、組合或封裝成輸出 XML 文件。|  
|XMLDasm.exe|執行 XML 解譯器元件，並透過模擬接收管線直接叫用該元件，讓您能夠查看它如何將使用者的 XML 文件剖析、解譯或解除封裝成一或多份 XML 文件。|  
  
 如需有關中可用的公用程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SDK，請參閱[SDK 中的公用程式](http://go.microsoft.com/fwlink/?LinkId=154387)(http://go.microsoft.com/fwlink/?LinkId=154387)。  
  
## <a name="see-also"></a>請參閱  
 [測試的工具](~/technical-guides/tools-for-testing.md)