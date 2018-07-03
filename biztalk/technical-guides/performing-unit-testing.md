---
title: 執行單元測試 |Microsoft Docs
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
ms.openlocfilehash: 36ede86266ea02b05249aa3edd655f3b10a27f3a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007583"
---
# <a name="performing-unit-testing"></a>執行單元測試
單元測試將焦點放在元件層級，以及基本上就是確認如預期般，是否要執行的 BizTalk 方案的個別元件的通過/失敗測試。 您有針對單元測試 BizTalk 解決方案的數個選項。  

## <a name="using-visual-studio"></a>使用 Visual Studio  
 適用於 Visual Studio 2008 和更新版本的單元測試功能。 如需適用於 Visual Studio 的測試功能的詳細資訊，請參閱[測試應用程式](http://go.microsoft.com/fwlink/?LinkId=159595)(http://go.microsoft.com/fwlink/?LinkId=159595)。  

 BizTalk Server 也提供單元測試功能讓使用者能夠建立結構描述、 對應和管線的單元測試。 如需這項功能的詳細資訊，請參閱[單元測試使用 BizTalk Server 專案](http://go.microsoft.com/fwlink/?LinkId=158270)(http://go.microsoft.com/fwlink/?LinkId=158270)。  

> [!NOTE]  
>  Visual Studio 是非常適用於單元測試 BizTalk 成品，例如協調流程、 結構描述、 管線和管線元件。 BizTalk Server 會提供測試類別，您可以搭配 Visual Studio Team System 測試 BizTalk 成品。  

## <a name="using-non-microsoft-tools"></a>使用非 Microsoft 工具  
 兩個其他常用的工具進行單元測試 BizTalk 解決方案**BizUnit**並**NUnit**。 **BizUnit**完美搭配 Visual Studio Team System Test Edition。 同樣地， **NUnit**測試可以輕鬆地修改，以便它們可以當做執行-在 Visual Studio Team System Test Edition。 如需有關這些工具的詳細資訊，請參閱 <<c0> [ 工具測試](~/technical-guides/tools-for-testing.md)。  

> [!NOTE]  
>  使用**BizUnit**並**NUnit**不會受到 Microsoft，而且 Microsoft 對於不保證這些程式的適用性。 請自行承擔使用這些程式的一切風險。  

## <a name="using-the-biztalk-server-sdk"></a>使用 BizTalk Server SDK  
 您可以執行單元測試中可用的公用程式使用個別的 BizTalk 成品[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SDK。 下表提供可用於單元測試的 SDK 中的公用程式的摘要：  


|    **公用程式**     |                                                                                                                                                                                                                                                                   **目的**                                                                                                                                                                                                                                                                   |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AS2 傳送者公用程式 |                                                                                                                                                                                              可讓您將 AS2 訊息傳送至單一電腦上的網站。 這個公用程式可模擬從個別電腦傳送 AS2 訊息的動作。                                                                                                                                                                                              |
|     DSDump.exe     |                                                                                  可讓您傾印文件結構描述結構，也就是一或多個 XSD 結構描述在記憶體中的輕量型表示法 (不論是否有一般檔案註解)。 當您發生剖析引擎錯誤 (例如 $Root$0$3$2) 且需要將錯誤解碼時，這個工具就很有用。 $ 後面的數字代表出現在文件結構描述中以 0 為基礎的索引或記錄。                                                                                   |
|     FFAsm.exe      |                                                                                                                                                                        執行一般檔案組合器元件，並透過模擬傳送管線直接叫用該元件，讓您能夠查看它如何將使用者的 XML 文件序列化或組合成一般檔案文件。                                                                                                                                                                        |
|     FFDasm.exe     |                                                                                                                                                                 執行一般檔案解譯器元件，並透過模擬接收管線直接叫用該元件，讓您能夠查看它如何剖析或是將使用者的一般檔案文件解譯成一或多個 XML 文件。                                                                                                                                                                  |
|    Pipeline.exe    | 執行傳送或接收管線;接受一或多個輸入的文件及其組件、 XSD 結構描述和相關的資訊;並會產生輸出文件的管線之後執行。 Pipeline.exe 不會存取[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，因此包含存取的 BizTalk Framework 組合器和解譯器元件的管線[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可能不支援在執行期間的資料庫。 |
|     XMLAsm.exe     |                                                                                                                                                                    執行 XML 組合器元件，並透過模擬傳送管線直接叫用該元件，讓您能夠查看它如何將使用者的 XML 文件序列化、組合或封裝成輸出 XML 文件。                                                                                                                                                                    |
|    XMLDasm.exe     |                                                                                                                                                                執行 XML 解譯器元件，並透過模擬接收管線直接叫用該元件，讓您能夠查看它如何將使用者的 XML 文件剖析、解譯或解除封裝成一或多份 XML 文件。                                                                                                                                                                |

 如需有關在可用的公用程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SDK，請參閱 < [SDK 中的公用程式](http://go.microsoft.com/fwlink/?LinkId=154387)(<http://go.microsoft.com/fwlink/?LinkId=154387>)。  

## <a name="see-also"></a>另請參閱  
 [測試的工具](~/technical-guides/tools-for-testing.md)