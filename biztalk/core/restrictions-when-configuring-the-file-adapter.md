---
title: 設定 File 配接器時的限制 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [File adapters], restrictions
- File adapters, restrictions
ms.assetid: 8d8137a7-5b16-4ae3-a0a7-6d114324bdf3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6fbf9296e56db816277f9a7a348377bfa4b359d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975126"
---
# <a name="restrictions-when-configuring-the-file-adapter"></a>設定 File 配接器時的限制
限制和規則時使用 file 配接器。

## <a name="file-mask-and-file-name-gotchas"></a>檔案遮罩和檔案名稱有什麼陷阱

檔案遮罩是一個字串，指定 FILE 接收處理常式從接收位置拾取的檔案類型。 檔案名稱是一個字串，指定 FILE 傳送處理常式寫入訊息的檔案名稱。  
  
 下列限制適用於檔案名稱和檔案遮罩屬性：  
  
-   每個接收位置或傳送埠只能指定一個檔案遮罩或一個檔案名稱。  
  
-   不允許完整路徑或部分路徑加上檔案遮罩或檔案名稱。 檔案遮罩和檔案名稱永遠代表不含路徑的名稱。  
  
-   檔案遮罩和檔案名稱不區分大小寫。  
  
-   檔案名稱不能包含任何下列字元： \< \> : / &#124;" ? * ;  
  
-   檔案遮罩不能包含任何下列字元： \< \> : / &#124;" ; 
  
-   下列保留的裝置名稱不能做為檔案名稱： CON、 PRN、 AUX、 時鐘 $、 NUL、 COM1、 COM2、 COM3、 COM4、 COM5、 COM6、 COM7、 COM8、 COM9、 LPT1、 LPT2、 LPT3、 LPT4、 LPT5、 LPT6、 LPT7、 LPT8 和 LPT9。 此外，也不允許這些名稱與副檔名的任何組合。  
  
-   Windows 磁碟區使用的預設值，就會使用短期或長期的檔案名稱來命名慣例 8.3 (8.3)。 非系統磁碟區停用 8.3 命名慣例，而且因此只會使用長檔名。 

    8.3 啟用時，檔案和其副檔名會取得轉換成簡短名稱。 例如，`testabcdefgh.docx`取得轉換成`testab~1.doc`。 請注意，會縮短檔案名稱，而檔案延伸模組會縮短從`.docx`至`doc`。

    此行為會影響如何 File 配接器接收檔案。 如果檔案遮罩之所以設為`*.xml`，然後檔案 比對兩者`*.xml`和`*.xmln`收取擴充功能。 

    若要查看您的磁碟上是否已啟用 8.3 命名慣例，請開啟命令提示字元當做系統管理員，並使用 type `fsutil 8dot3name query c:`，或`fsutil 8dot3name query d:`，依此類推。 範例輸出如下所示：

    ```
    C:\WINDOWS\system32>fsutil 8dot3name query c:
    The volume state is: 0 (8dot3 name creation is enabled).
    The registry state is: 2 (Per volume setting - the default).
    
    Based on the above two settings, 8dot3 name creation is enabled on c:
    ```
    
    File 配接器使用[FindFirstFile 函式](https://msdn.microsoft.com/library/windows/desktop/aa364418(v=vs.85).aspx)。 此函式會包含具有短期或長期的檔案名稱的搜尋結果。 若要查看資料夾中的短期或長期的檔案名稱，開啟命令提示字元，請前往您的資料夾，並輸入`dir /x`。 在命令提示字元中，您也可以輸入`dir c:\foldername /x`。
    
    如果您變更 8dot3name 設定磁碟區上的時，新的檔案就會使用新的設定。 任何現有的檔案會保留其名稱，直到它們會移動。 
    
    若要只收取您預期的檔案，並在更高的負載期間取得較佳的效能 （較少額外負荷），則可能過最佳設定來使用的磁碟區會在停用 8dot3name File 配接器。 
  
-   檔案路徑、檔案遮罩和檔案名稱 (不含巨集替代) 的總長度不可超過 256 個字元。 (這是 MessageBox 資料庫的限制。)  
  
-   檔案路徑不能以 "`\\`?" 開頭。  
  
-   對應的網路磁碟機代號不能用於檔案路徑，因為他們是以使用者工作階段為基礎。  
  
 「BizTalk 傳訊引擎」永遠會使用先前列示的項目，在設計階段驗證檔案名稱和檔案遮罩屬性。 此外，若配接器在動態連接埠上傳送訊息，FILE 配接器會在執行階段驗證檔案名稱和檔案遮罩屬性。  
  
> [!NOTE]
>  FILE 配接器不會拾取系統檔案或唯讀檔案。 只會拾取硬碟的檔案，不會拾取裝置檔案。  

## <a name="using-macros-in-file-names"></a>在 檔案名稱使用巨集

您可以使用一組預先定義的巨集，以動態建立 FILE 傳送處理常式在其中寫入訊息的檔案。 在檔案系統上建立檔案之前，FILE 傳送處理常式會以其個別的值取代檔案名稱中的所有巨集。 您可以在一個檔案名稱中使用數個不同的巨集。  
  
 在使用 BizTalk 總管物件模型設定 FILE 傳送處理常式時，可以使用檔案名稱巨集。  
  
 若發生下列任何一種情況，FILE 傳送處理常式就不會以值取代巨集：  
  
-   未設定對應的系統屬性。  
  
-   巨集拼錯。  
  
-   巨集的值包含檔案名稱中無效的符號。  
  
 若發生這些情況中的任何一項，FILE 傳送處理常式就會將檔案名稱中的巨集保留原狀，例如 Myfile_%MessageID%.xml。  
  
 下表列出支援的巨集，並描述 FILE 傳送處理常式如何取代它們。  
  
|巨集名稱|取代值|  
|----------------|----------------------|  
|%datetime%|Coordinated Universal Time (UTC) 日期時間格式為 YYYY-MM-DDThhmmss (例如，1997-07-12T103508)。|  
|%datetime_bts2000%|UTC 日期時間的格式為 YYYYMMDDhhmmsss，其中 sss 表示秒與毫秒 (例如，199707121035234 表示 1997/07/12，10:35:23 與 400 毫秒)。|  
|%datetime.tz%|本地日期時間加上 GMT 的時區，格式為 YYYY-MM-DDThhmmssTZD (例如，1997-07-12T103508+800)。|  
|%DestinationParty%|目的地合作對象的名稱。 這個值來自訊息內容屬性 **BTS.DestinationParty**。|  
|%DestinationPartyQualifier%|目的地合作對象的辨識符號。 這個值來自訊息內容屬性 **BTS.DestinationPartyQualifier**。|  
|%MessageID%|BizTalk Server 中訊息的全域唯一識別碼 (GUID)。 值是直接來自訊息內容屬性**BTS。MessageID**。|  
|%SourceFileName%|FILE 配接器從中讀取訊息的檔案名稱。 檔案名稱包含副檔名但排除檔案路徑，例如 Sample.xml。 File 配接器時取代這個屬性，從儲存在的絕對檔案路徑擷取檔案名稱**檔案。ReceivedFileName**內容屬性。 如果內容屬性沒有值 — 比方說，如果在 File 配接器以外的配接器收到的訊息-巨集將不會被取代，並將保留在檔案名稱 (例如 C:\Drop\\%sourcefilename%)。 **注意：** 正確實作此巨集需要的輸出訊息和接收的訊息相同的訊息。|  
|%SourceParty%|FILE 配接器從中接收訊息的來源合作對象名稱。 **注意：** 正確實作此巨集需要的輸出訊息和接收的訊息相同的訊息。|  
|%SourcePartyQualifier%|FILE 配接器從中接收訊息的來源合作對象辨識符號。 **注意：** 正確實作此巨集需要的輸出訊息和接收的訊息相同的訊息。|  
|%time%|UTC 時間的格式為 hhmmss。|  
|%time.tz%|本地時間加上 GMT 的時區，格式為 hhmmssTZD (例如，124525+530)。|  
  
 
## <a name="receive-folder-and-destination-location-properties-gotchas"></a>接收資料夾和目的地位置屬性有什麼陷阱

檔案接收位置是一個包含檔案系統或網路共用上之資料夾路徑的字串，而 FILE 接收處理常式會從此路徑讀取檔案。 檔案目的地位置是一個包含檔案系統或網路共用上之資料夾路徑的字串，而 FILE 傳送處理常式會從此路徑寫入檔案。  
  
 下列限制適用於接收資料夾和目的地位置屬性：  
  
-   在您指定使用者中的屬性時，不需要有檔案系統或網路共用上的檔案路徑存在。  
  
-   檔案路徑必須永遠是絕對路徑。  
  
-   您可以藉由使用通用命名慣例 (UNC) 格式來指定檔案路徑 (例如， \\ \\ <*伺服器*\> \\ < *共用*\>)。  
  
-   如果檔案路徑為 UNC 格式，伺服器名稱必須包含下列字元: ' ~ ！ @ # $ ^ & * ( ) = + [ ] { } \ &#124; ; : ' " , \< \> / ? ;  
  
-   您無法使用父 (\\..\\) 和目前 (\\。\\) 資料夾符號中的檔案路徑的任何部分。  
  
-   檔案路徑是不區分大小寫的。  
  
-   檔案路徑不能包含任何下列字元： \< \> : / &#124;" ? * ;  
  
-   檔案路徑內不能使用下列保留的裝置名稱：CON、PRN、AUX、CLOCK$、NUL、COM1、COM2、COM3、COM4、COM5、COM6、COM7、COM8、COM9、LPT1、LPT2、LPT3、LPT4、LPT5、LPT6、LPT7、LPT8 和 LPT9。  
  
-   檔案路徑、檔案遮罩或檔案名稱 (沒有巨集替代) 的總長度不得超過 256 個字元。 (MessageBox 資料庫設有此限制。)  
  
-   File 配接器不支援 Unicode 規格的檔案路徑 (例如，"\\\\？\\")。  
  
 在接收配接器屬性上的限制只有：  
  
-   務必為接收資料夾屬性設定為使用含有符號連結的 Microsoft Windows NT 分散式檔案系統資料夾。 如果您使用 Windows NT 分散式檔案系統，您只能使用資料夾含有直接網路路徑中檔案配接器接收位置。  
  
-   當文件傳送到 UNC 路徑，而且您有一部以上的伺服器在 FILE 配接器的接收位置上接收文件時，則只有一部伺服器會收取和處理傳送至該 UNC 路徑的大部分文件。 如需檔案重新命名的詳細資訊，請參閱 > 一節 File 接收配接器[File 配接器](../core/file-adapter.md)。  
  
 僅針對傳送資料夾屬性的限制：  
  
-   當 FILE 配接器在非伺服器的作業系統 (例如 Microsoft Windows Vista) 上執行時，可能沒有足夠的作業系統資源能同時處理批次中的全部訊息。  
  
 FILE 配接器會使用先前提及的規則，於設計階段驗證檔案路徑。 此外，若配接器會以 FILE 配接器透過動態連接埠來傳送訊息，則 FILE 配接器會在執行階段驗證訊息。  
  
