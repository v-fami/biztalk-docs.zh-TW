---
title: 定義商務程序 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e5e0fdfe-e298-4f32-a7c5-d081b926a206
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6776b78b06e68b67e9391d4f3fb1ddf64db72198
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22243270"
---
# <a name="defining-business-processes"></a>定義商務程序
不同系統之間的訊息交換是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 著重要解決的問題之必要部分。 不過，真正的目標是定義並執行以這些應用程式為基礎的商務程序。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 引擎使用協調流程來定義商務程序的邏輯。 若要建立和評估商務規則群組，會使用「商務規則引擎」。 本節會說明協調流程及「商務規則引擎」。  
  
## <a name="using-orchestrations"></a>使用協調流程  
 自動商務程序的邏輯可直接以 Microsoft Visual Basic 或 Microsoft Visual C# 這類語言實作。 不過，以傳統程式語言建立、維護以及管理複雜的商務程序是一大挑戰。 不同於之前的版本，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 採用了不同的方法。 可讓商務經理人或開發人員以圖形化方式定義商務程序。 這樣會比直接用程式語言建立商務程序更快速，而且更易於瞭解、說明和變更程序。 拜「商務活動監控」(BAM) 技術之賜，以此方法建置的商務程序也更易於監控。  
  
 針對開發人員，會建立協調流程依賴三個主要工具: [BizTalk 編輯器] 來建立 XML 結構描述，BizTalk 對應工具來定義這些結構描述，與指定的商務邏輯的協調流程設計師 」 之間的翻譯處理程序。 這些工具全部位於 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 內，為開發人員提供一致性的環境。 此節會敘述這些工具的功能以及它們如何共同作業。  
  
### <a name="creating-schemas-the-biztalk-editor"></a>建立結構描述: 「 BizTalk 編輯器  
 協調流程使用 XML 文件，每一個都符合部分 XML 結構描述。 開發人員可以使用「BizTalk 編輯器」來定義這些結構描述，而這些結構描述基本上是使用 XML 結構描述定義語言 (XSD) 定義文件資訊的結構及類型。  
  
 不使用工具支援來建立原始 XSD 結構描述是一大挑戰。 為了更容易實行此必要步驟，BizTalk 編輯器允許使用者 (可能是開發人員) 以圖形階層方式定義元素，以建立結構描述。 您也可以從檔案或者可存取的 Web 服務匯入現有的結構描述。 無論如何取得，結構描述都是 BizTalk 對應的基礎。  
  
### <a name="mapping-between-schemas-the-biztalk-mapper"></a>BizTalk 對應的結構描述之間的對應：  
 一個實作商務程序的協調流程，一般來說會收到某些文件並傳送其他文件。 通常接收文件中的部分資訊會轉送至傳送文件，也許在某些方面有點改變。 例如，訂單履行程序可能收到一些項目的訂單，然後傳回因為某些原因訂單已被拒絕的訊息。 像是要求識別項及訂購數量等的訂單資訊，可從接收訂單訊息的欄位複製到拒絕訊息欄位中。 BizTalk 對應工具可用來定義在文件間的轉換，稱為對應。  
  
 ![結構描述之間的對應](../core/media/understandingbts-2010-mapper.gif "UnderstandingBTS_2010_Mapper")  
  
 如上圖所示，每個對應都會以圖形化相互關聯顯示在兩個 XML 結構描述中，且對應會定義這些結構描述中元素間的關係。 「全球資訊網協會」(W3C) 已定義「可延伸樣式表語言轉換」(XSLT) 做為在 XML 結構描述之間轉換的標準方法，所以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的對應會以 XSLT 轉換的形式實作。  
  
 在對應中定義的轉換可以很簡單，例如從某一文件複製值到其他文件，沒有任何變更。 像這種直接的資料複製可用連結表示，該連結在 BizTalk 對應工具中顯示成一條連接來源結構描述適當元素，以及在目的結構描述的相應元素之間的線條。 使用運算質也可以進行更複雜的轉換。 運算質是大量可執行的程式碼，可任意定義 XML 結構描述間的複雜對應，且如上圖所示，BizTalk 對應工具會將其表示為連線轉換元素線條上的方塊。 因為某些轉換相當普通，所以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含一些內建的運算質。 這些內建運算質劃分成多個類別，包括以下各項：  
  
-   執行計算的數學運算質，像是加、減、乘、除來源文件中的欄位值，以及將結果儲存至目標文件中的欄位。  
  
-   將數值轉換成 ASCII 相對值的轉換運算質，反之亦然。  
  
-   邏輯運算質，利用邏輯比較來源文件中特定的值，來決定元素或屬性是否應該建立在目標文件中。 可以用等於、大於小於或其他方式來比較這些值。  
  
-   累計運算質，計算平均值、總計或其他來源文件不同欄位的值，然後將結果儲存至目標文件中的單一欄位。  
  
-   可存取儲存在資料庫中的資訊之資料庫運算質。  
  
 您也可以直接在 XSLT 中，或使用像 Visual C# 及 Visual Basic 這類支援 .NET 的語言，建立自訂運算質。 運算質也可以按照順序結合，將其中一個的輸出排列在其他的輸入下方。  
  
 重要的是要有方法可定義文件的 XML 結構描述，以及對應不同結構描述的多個文件資訊的機制。 BizTalk 編輯器和 BizTalk 對應工具可解決這兩個問題。 但是定義結構描述及對應只是程序的一部分而已。 您還必須指定會使用結構描述與叫用對應的商務邏輯。  
  
### <a name="defining-business-logic-the-orchestration-designer"></a>定義商務邏輯： 協調流程設計師  
 商務程序是一組動作，結合後滿足某些商務需求。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，開發人員可以使用「協調流程設計師」，以圖形方式定義這些動作。 此工具不使用某些程式語言來表達步驟，開發人員可以用邏輯的方式，將一系列圖形連接在一起以建立協調流程。 「協調流程設計師」中可用的圖形包含：  
  
-   接收圖形，讓協調流程接收訊息。 接收圖形可具有定義要接收之訊息類型的篩選，也可以設定為當新訊息到達時便啟動新的協調流程執行個體。  
  
-   傳送圖形，讓協調流程傳送訊息。  
  
-   連接埠圖形，定義訊息傳輸的方式。 連接埠圖形的每個執行個體若不是連接到傳送圖形就是連接到接收圖形。 每個連接埠也都有類型，可定義連接埠可接收的訊息類型；方向，如傳送或接收；繫結，可決定傳送或接收訊息的方法，如指定特定 URL 及其他資訊。  
  
-   決定圖形代表 if-then-else 陳述式，可以讓協調流程根據布林值條件執行不同工作。 運算式編輯器是協調流程設計師的一部分，可用來指定此條件陳述式。  
  
-   迴圈圖形，在某些條件為真時控制動作的重複執行。  
  
-   建構訊息圖形，可建置訊息。  
  
-   傳輸圖形，可將一個文件的資訊傳輸到另一個文件，並叫用 BizTalk 對應工具定義的對應進行傳輸。  
  
-   平行動作圖形，可讓開發人員指定應平行執行而不是以序列方式執行的多個作業。 所有平行動作完成後，之後的圖形才可以執行。  
  
-   範圍圖形，允許一組作業進入交易，並定義錯誤處理的例外狀況處理常式。 支援傳統的不可部分完成交易及長時間執行交易。 與不可部分完成交易不同，長時間執行交易依賴補償邏輯而非回復以處理未預期的事件。  
  
-   訊息指派圖形，可指派值到協調流程變數。 這些變數可用來儲存協調流程使用的狀態資訊，如建立的訊息或字元字串。  
  
 下圖顯示使用少數這些圖形在協調流程設計師建立的協調流程。 在這個簡單的範例中，已收到訊息並已根據訊息的內容制訂決策，結果是執行兩個路徑中的其中一個。 解決真正問題的協調流程可能會比這個範例更為複雜；為了便於使用更複雜的圖表，協調流程設計師還有放大和縮小功能。開發人員可以只檢視他們目前在協調流程中感興趣的那些部分。  
  
 ![](../core/media/understandingbts-08-orchestration.gif "UnderstandingBTS_08_Orchestration")  
  
 開發人員定義協調流程後，圖形群組及圖形之間的關係會轉換為 .NET Framework 之 Common Language Runtime (CLR) 使用的 Microsoft Intermediate Language (MSIL)。 最後，BizTalk Server 開發人員定義的圖形群組會變成啟用 .NET 的標準組件。 當需要從圖形內呼叫 COM 或 .NET 物件時，您也可以新增明確的程式碼到協調流程中。  
  
### <a name="the-role-of-web-services"></a>Web 服務的角色  
 Web 服務可讓應用程式使用 SOAP 交換 XML 文件，並在整合平台中具有重要的影響。 若要存取外部 Web 服務，協調流程的建立者可使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中的 [加入 Web 參考] 選項及 Web 服務配接器直接叫用作業。 同樣地，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供 Web 服務發佈精靈，可以產生 ASP.NET Web 服務專案，將一或多個協調流程作業公佈為 SOAP 可呼叫的 Web 服務。 這兩個選項可以讓開發人員從商務程序存取現有的 Web 服務，以及將協調流程的功能公佈成其他商務程序的 Web 服務。  
  
-   Web 服務的崛起對定義商務程序的方式有重大的影響。 例如，想像兩個組織使用 Web 服務互動的案例。 為了更有效率的互通，可能需要每個互動的合作對象都瞭解另一方使用的商務程序。 若兩個組織都使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，這就不是大問題；可以使用交易夥伴管理技術等工具來傳遞這項資訊。 但是若他們使用不同產品呢？ 這時能以非廠商指定的方式來描述商務程序的概念就很有用了。  
  
 為此，Microsoft、IBM 及其他廠商已經建立商務程序執行語言 (BPEL)。 使用協調流程設計師定義的商務程序可以匯出為 BPEL，而且 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 也可以匯入以 BPEL 定義的程序。 此語言可用來描述並共用商務程序外部的可見組件，而 BPEL 則著重在解決這個問題，而不是跨平台的完整執行商務程序。 也請務必瞭解 BPEL 是完全建置在 Web 服務上，而支援此語言的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 及其他產品則可提供更多功能。 例如，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援不同 XML 結構描述之間的對應、在本機物件呼叫方法以及 BPEL 不提供的其他功能。 諸如以上及其他種種原因，BPEL 不是用來定義商務程序的完整語言。 且由於 BPEL 仍處於 Organization for the Advancement of Structured Information Standards (OASIS) 加以標準化的階段，因此目前還很難將其視為完全成熟的技術。  
  
-   協調流程是在 BizTalk Server 中建立商務程序的基礎機制。 但協調流程中有某些方面的變更頻率特別高。 特別是，商務程序中的決策 (商務規則) 通常是最常變動的部分。 管理員的消費限制為 $100000 過去一週，但升遷到 $500000 或從 100 單位至 10 的延遲付款客戶最大允許的順序減少。 您可以指定並更新這些使用 「 商務規則引擎的規則。  
  
## <a name="using-the-business-rule-engine"></a>使用商務規則引擎  
 協調流程設計師加上 BizTalk 編輯器和 BizTalk 對應工具，提供有效的方法以定義商務程序及其使用的規則。 不過，若有更簡單的方法可定義及變更商務規則，它就更實用了。 為此，BizTalk Server 提供了「商務規則引擎」(BRE)。 開發人員通常會使用 BRE，但是商務導向的使用者可使用名為「商務規則編輯器」的工具建立和修改商務規則組。  
  
 當必須評估複雜的商務規則組時，BRE 就很有用。 例如，決定是否要同意借款，可能必須根據客戶的信用記錄、收入及其他因素來使用大量規則組。 同樣的，決定是否將壽險賣給保險人也需要根據幾個因素，包括保險人的年紀、性別及健康狀況。 透過協調流程的「決定」圖形等方式將這些規則皆呈現為條件陳述式或許是可行的，但是實作上會相當複雜。 在這樣充滿大量規則的程序中，BRE 可簡化開發人員的工作。  
  
 使用 BRE，開發人員可視需要快速輕鬆地變更規則。 若要瞭解原因，請試想變更在協調流程中實作的商務規則所需要的條件為何？ 開發人員必須先在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中開啟協調流程、修改適當的圖形 (可能還包括圖形所叫用的 .NET 或 COM 物件)，然後建置並部署修改的組件。 這些工作還需要停止並重新啟動包含此協調流程的 BizTalk 應用程式。 若是使用 BRE 實作商務規則，無須重新編譯或重新啟動任何應用程式就可以進行修改。 您僅需要使用「商務規則編輯器」變更想要的規則，然後重新部署新的規則組。 變更會立即生效。 而且雖然協調流程一般是由開發人員建立和維護的，但在某些情況下商務分析師可自行理解商務規則並進行修改，無須技術人員協助。  
  
 商務規則組的建立者一般會使用「商務規則編輯器」開始，以定義用來指定這些規則的詞彙。 詞彙中的每一個名詞提供部分資訊的易記名稱。 例如，詞彙可能會定義像「出貨量」或「項目的數量上限」或「核准限制」等術語。 這些術語可各自設定為常數，或對應到某個 XML 結構描述中的特定元素或屬性中 (因此也會在內送訊息中)，或對應到某些資料庫的 SQL 查詢結果，或甚至 .NET 物件中的值。  
  
 詞彙定義完成後，「商務規則編輯器」可用來建立使用此詞彙的商務原則。 每一個原則可包含一或多個商務規則。 規則會使用某些詞彙中定義的術語及邏輯運算子，如 Greater Than、Less Than、Is Equal To 及其他運算子來定義商務程序運作的方式。 商務規則可定義接收 XML 文件中包含的值對傳送 XML 文件內所建立之值的影響，或這些接收值對寫入資料庫中之值的影響，或其他等等。  
  
 為了執行商務原則，協調流程會使用 CallRules 圖形。 這個圖形建立 BRE 的執行個體、指定要執行的原則，然後傳遞此原則需要的資訊，如接收的 XML 文件。 也可使用以 .NET 為基礎的物件模型以程式設計方式叫用 BRE，這樣可讓不是使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的應用程式呼叫 BRE。 這表示該 Windows Forms 應用程式、 軟體公開 Web 服務和其他建置在.NET Framework 上的任何項目可能 BRE 無論何時可以使用它可協助解決問題的實力。  
  
 詞彙和商務規則都可能比這裡所描述的簡單範例更為複雜且功能更多。 但定義詞彙、然後定義規則來使用詞彙的基本觀念，乃是「商務規則引擎」的核心。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 傳訊引擎](../core/the-biztalk-server-messaging-engine.md)