---
title: 設計 BizTalk 應用程式的國際化考量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9daaaaf7-6149-4e62-9e9b-b6356fc820d2
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ef22467c18580219e8587d63017d8bf146090d4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974572"
---
# <a name="international-considerations-for-designing-biztalk-applications"></a>設計 BizTalk 應用程式的國際化考量
強烈建議您在開發國際化 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式時，最好先檢閱下列已知問題。  
  
 **電腦名稱的字元限制**  
  
 安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不支援包含下列集之外的字母的電腦名稱上： 英文字母 （A 到 Z、 a 到 z）、 數字 (0-9)、 連字號 （-） 和底線 (_)。 只支援電腦名稱包含上述字母的電腦。  
  
 **字元未正確顯示，或沒有出現，因為不正確的字型和字型遞補設定**  
  
 在裝載於 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 工具中，可能會遇到字元顯示的問題 (如捷克文字元)。 為了對付這些問題，您可能需要修改 Visual Studio [選項] 索引標籤上所提供的字型設定，並選取您知道可支援這些字元的另一種字型。 當有提供字型遞補功能時，您可以選取 Tahoma 或 Microsoft Sans Serif 當做預設字型。  
  
 **Surrogate 字組字元顯示為方塊在 BizTalk Server 管理主控台和其他 BizTalk Server 工具**  
  
 您可能無法在 BizTalk Server 管理主控台和其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 工具中顯示 Surrogate 字組字元。 Surrogate 字組是單一抽象字元 (由兩個字碼單位組成) 的編碼字元表示。 請確定系統上有安裝適當的字型 (中文版的 Office XP 和 2003 中有包括)。 您也可能需要在具有這類功能的工具 (如 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]) 中變更其字型選項。  
  
 在沒有字型設定選項的其他工具中，Surrogate 字組字元將會顯示為方塊字元 (例如在管理主控台中)。 如果您看到方塊，這些字元並未損毀，而只是因為缺少字型支援而無法正確顯示。  
  
 **Web 服務字元限制**  
  
 如果您打算將協調流程發佈為 Web 服務，您可能會遇到協調流程名稱和連接埠名稱中使用之字元的問題，因為這些名稱會用於 Web 服務檔案名稱 (.asmx 檔案) 和「Web 服務發佈精靈」中的虛擬目錄。 只有 Microsoft Internet Information Services (IIS) 7.0 (隨附於 Microsoft Windows Server 2008 與 Windows Vista 中) 可完全支援 Unicode 字元； 因此，如果您使用舊版的 IIS 或 Windows，則協調流程、連接埠、Web 服務和虛擬目錄的名稱必須只包含該 Windows 語言版本所支援的 ANSI 字元 (例如，不允許在英文版的 Windows 上使用日文字元)。  
  
 也請注意一點，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中 Web 服務的專案名稱限制為 ASCII 字元。  
  
 **使用不同的文件編碼**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援 XML 和一般檔案文件的許多不同編碼方式，例如 UTF-16、UTF-8、簡體中文 (GBK)、簡體中文 (GB18030) 等等。  
  
 輸入文件，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以辨識的編碼方式宣告在 XML 文件，例如"\<？ xml 版本 ="1.0"encoding ="GB2312"？\>"。 一般檔案結構描述具有**字碼頁**屬性，表示內送一般檔案文件的編碼方式。  
  
 輸出文件、 XML 和一般檔案組合器使用**目標字元集**屬性。 如果指定了這個屬性，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會將輸出文件轉換成指定的字元集，而不論原始的字元集為何。 如果沒有**目標字元集**屬性設定，XML 會使用 utf-8 通訊協定和一般檔案會使用一般檔案結構描述中指定的字碼頁。  
  
 **程式碼從支援的字碼頁轉換成 Windows 字碼頁**  
  
 若要實作字碼轉換，從不支援的字碼頁轉換成 Windows 字碼頁，您必須建立自訂管線元件。  
  
 **位元組順序標示對於文件編碼**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會判斷字元編碼方式，並使用特定的字元編碼方式 (一般檔案和 XML 訊息會有所不同) 來產生文件。  
  
 **結構描述編輯器可能會包含在一個以上的語言中的屬性**  
  
 顯示於 [結構描述編輯器屬性] 視窗和 XML 原始程式碼中的 XML 結構描述定義語言 (XSD) 屬性名稱不會當地語系化，所有當地語系化的版本中都會顯示英文。 其他的屬性則會以當地語言顯示。 例如，在簡體中文版的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，結構描述屬性為英文，但是其他屬性則顯示為中文。  
  
 **一般檔案中的地區設定相關資料**  
  
 許多地區設定代表類似日期、時間、數字和貨幣等資料，這些資料使用的格式與 XML 標準中定義的格式不同。 例如，有數種地區設定使用句號 (.) 以外的小數分隔符號，所以五點七五這個數字可能會表示為 5,75。  
  
 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，一般檔案中的所有欄位 (日期和時間除外) 會視為字串，所以剖析可以成功。 但是當使用 XML 驗證時，在針對結構描述進行驗證的期間，產生的 XML 訊息會發生失敗。  
  
 如果是日期和時間欄位，剖析器會嘗試將欄位值剖析為使用自訂日期或時間格式 (若有定義) 的日期時間執行個體，並以 XML 格式寫入它，或使用原始值當做字串 (如果未定義日期或時間格式)。 同樣地，如果使用了 XML 驗證，當未使用自訂日期或時間格式，而且一般檔案訊息中使用的欄位值未使用正確的 XML 日期或時間格式時，產生的日期或時間可能會驗證失敗。  
  
 請注意，您也可以建立自訂管線元件或對應來更新欄位值，以產生有效的 XML。  
  
 **BAM 定義語言支援**  
  
 在您可以部署 BAM 定義 XML 檔之前，您必須確定用來建立此檔案的語言與其部署所在之電腦的地區設定一致。 如果此檔案和電腦設定不相符，您必須先將用來執行 BM.exe 的電腦重新開機。  
  
> [!NOTE]
>  除非所有的語言都使用相同的字碼頁，或只使用兩種語言且其中之一為英文，否則 BAM 定義 XML 檔不可包含多種語言的文字。  
  
## <a name="see-also"></a>請參閱  
 [實作管線元件中的字元編碼方式](../core/implementing-character-encoding-in-a-pipeline-component.md)   
 [處理解譯器管線元件中的編碼](../core/handling-encoding-in-a-disassembler-pipeline-component.md)   
 [一般檔案解譯器管線元件中的字元編碼](../core/character-encoding-in-the-flat-file-disassembler-pipeline-component.md)   
 [一般檔案組合器管線元件中的字元編碼](../core/character-encoding-in-the-flat-file-assembler-pipeline-component.md)   
 [XML 組合器管線元件中的字元編碼](../core/character-encoding-in-the-xml-assembler-pipeline-component.md)   
 [XML 解譯器管線元件中的字元編碼](../core/character-encoding-in-xml-disassembler-pipeline-component.md)