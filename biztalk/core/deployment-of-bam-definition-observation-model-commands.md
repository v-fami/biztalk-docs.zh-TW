---
title: 部署 BAM 定義 （觀察模型） 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df7914f3-7a92-4ab2-bd0e-94a2eed4825e
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0dba1e1a4f54b3b33ebca8297cfe9beef7c4f868
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973188"
---
# <a name="deployment-of-bam-definition-observation-model-commands"></a>BAM 定義的部署 (觀察模型) 命令
BAM 管理公用程式部署命令可用來套用、修改和移除定義。  
  
-   deploy-all-definitionfile： 部署 BAM 定義。  
  
-   更新所有： 更新 BAM 定義。  
  
-   移除 all： 移除 BAM 定義。  
  
-   更新 livedataworkbook： 更新即時資料活頁簿中的資料庫連接資訊。  
  
-   重新產生 livedataworkbook： 重新產生即時資料活頁簿，伺服器上的。  
  
> [!NOTE]
>  您可以藉由啟用任何 BM 公用程式命令的追蹤 **-追蹤： 在 &#124; 關閉**切換參數。 使用追蹤參數會覆寫組態檔中的追蹤設定。 此參數可以搭配任何一般 BM 命令使用。  
  
> [!NOTE]
>  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="deploy-all-command"></a>deploy-all 命令  
 **使用方式**  
  
 **bm.exe deploy-all-definitionfile-DefinitionFile:\<def 檔\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|DefinitionFile:\<def 檔案\>|含有所要部署之定義的檔案所在路徑和名稱。|  
|伺服器：\<伺服器\>|選擇性： 要用來將定義部署的伺服器名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 要用來將定義部署的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 從指定的 BAM 定義 XML 檔案部署所有成品至指定的伺服器和資料庫。 檔案可以是包含 BAM 定義 XML 的文字檔或 BAM Excel 活頁簿。 定義檔必須只包含新成品。 如果檔案包含已部署的成品，部署將會失敗並報告錯誤。  
  
 **部署 BAM 定義的考量**  
  
 部署警示訂閱時，訂閱者的使用者識別碼必須指定成「網域\使用者」格式。  
  
 分散式的交易協調器 (DTC) 服務必須執行所在之電腦上**deploy-all-definitionfile**發出命令。  
  
 部署定義時，BAM 管理公用程式對於即時彙總 (RTA) 檢視僅支援 14 個維度層級。 部署的層級數若超出此限，將傳回「部署失敗」錯誤。  
  
 如果您用不同的語言設定來定義多個檢視，再將方案部署至採用單一語言的伺服器，就無法解除部署這些檢視。 唯有當任何的排程彙總都不需仰賴 BAM 定義提供 OLAP 的情況下，才支援這種做法。  
  
 如果啟用 BAM 警示，BAM 管理公用程式會將部署的活動檢視總數限制為 49 個。 活動檢視總數的計算方式為：各檢視分別乘以其上層活動的數目之後加總。  例如，如果您部署了涉及兩個活動的單一檢視，就視同兩個活動檢視。  假設您部署兩個檢視，其中之一跨越兩個活動，而另一檢視涉及單一活動，則總計為 3 個活動檢視。  
  
 如果 BAM 定義將多個樞紐分析表定義成相同的 RTA 與 Cube 名稱組合，BAM 管理公用程式會封鎖該定義的部署作業。 Bm.exe 將終止部署並傳回下列錯誤：  
  
 正在部署檢視...錯誤： BAM 部署失敗。  
  
 指定的 RTA 和 Cube 只能定義一個樞紐分析檢視。  
  
 以下所列的名稱都是保留字，如果使用將導致定義部署失敗：  
  
-   RecordID  
  
-   ActivityID  
  
-   IsVisible  
  
-   IsComplete  
  
-   LastModified  
  
> [!NOTE]
>  如果 bm.exe 在部署期間遇到錯誤，便會終止部署並將檢視和活動所做的變更回復。 OLAP Cube 所做的變更則不會回復，因為 OLAP 不支援交易式部署。  
  
> [!NOTE]
>  在採用某地區設定的電腦上所建立的 BAM 定義，只能部署至同樣設定為該地區設定的電腦。 例如，若在設定為英文地區設定的電腦上使用 Microsoft Excel 英文版產生 BAM 定義，就不能部署至採用日文地區設定的日文電腦。  
  
 **範例**  
  
```  
bm.exe deploy-all -DefinitionFile:MyDef.xml  
bm.exe deploy-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## <a name="update-all-command"></a>update-all 命令  
 **使用方式**  
  
 **bm.exe 更新所有-DefinitionFile:\<def 檔\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|DefinitionFile:\<def 檔案\>|含有執行更新所需之定義的檔案所在路徑和名稱。|  
|伺服器：\<伺服器\>|選擇性： 要部署定義更新的伺服器名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 要部署定義更新至資料庫的名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 從 BAM 定義 XML 更新特定成品。 檔案可以是包含 BAM 定義 XML 的文字檔或 BAM Excel 活頁簿。 更新不會刪除目前定義檔中未描述的成品。 這可將新的檢查點加入活動，但不能從已部署的活動卸除檢查點。 更新不能重新命名檢查點，也不能變更檢查點屬性。  
  
 一旦部署活動之後，可在活動上採取的動作便會受到限制。 特別是，您不可以從活動刪除項目，除非您準備請系統管理員解除部署整個 BAM 活動和檢視集，然後再重新部署。 這樣可能會造成暫時看不見資料或資料遺失，除非系統管理員執行資料備份與還原。  
  
> [!NOTE]
>  您無法使用此命令在現有的檢視中加入新活動。 若要在檢視中加入活動，您必須建立新檢視以包含新活動。 然後您就可以解除部署舊檢視，但須注意的是 OLAP 資料歷程記錄將隨之遺失。  
  
 **範例**  
  
```  
bm.exe update-all -DefinitionFile:MyDef.xml  
bm.exe update-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## <a name="remove-all-command"></a>remove-all 命令  
 **使用方式**  
  
 **bm.exe 移除 all DefinitionFile:\<def 檔\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|DefinitionFile:\<def 檔案\>|含有所要移除之定義的檔案所在路徑和名稱。|  
|伺服器：\<伺服器\>|選擇性： 移除定義的伺服器名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 移除定義的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 移除 BAM 定義 XML 檔案指定的所有成品。 檔案可以是包含 BAM 定義 XML 的文字檔或 BAM Excel 活頁簿。 每個成品的定義都必須完全符合用於部署的原始定義。  
  
 **範例**  
  
```  
bm.exe remove-all -DefinitionFile:MyDef.xml  
bm.exe remove-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## <a name="update-livedataworkbook-command"></a>update-livedataworkbook 命令  
 **使用方式**  
  
 **bm.exe 更新 livedataworkbook-名稱：\<即時資料活頁簿檔案名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|名稱：\<即時資料活頁簿\>|要更新的現有即時活頁簿的名稱。|  
|伺服器：\<伺服器\>|選擇性： 在活頁簿所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 在活頁簿所在資料庫的名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 更新指定的 BAM 即時資料活頁簿中的 BAM 主要匯入資料庫連線資訊。  
  
> [!NOTE]
>  在設定新的連線字串時，必須重新啟動 TDDS 服務以確保服務能辨識所做的變更。 如需 TDDS 服務的詳細資訊，請參閱[BAM 事件匯流排服務預存程序](../core/bam-event-bus-service-stored-procedures.md)。  
  
 **範例**  
  
```  
bm.exe update-livedataworkbook -Name:SalesManager_Live.xls  
bm.exe update-livedataworkbook -Name:SalesManager_Live.xls -Server:SalesSrv  
```  
  
## <a name="regenerate-livedataworkbook-command"></a>regenerate-livedataworkbook 命令  
 **使用方式**  
  
 **bm.exe regenerate livedataworkbook WorkbookName:\<即時資料活頁簿檔案名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|WorkbookName:\<即時資料活頁簿檔案名稱\>|要更新的活頁簿的名稱。|  
|伺服器：\<伺服器\>|選擇性： 在活頁簿所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 在活頁簿所在資料庫的名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 產生 BAM 即時資料活頁簿但不部署活頁簿。  
  
 範例  
  
```  
bm.exe regenerate-livedataworkbook -WorkbookName:SalesManager_Live.xls  
bm.exe regenerate-livedataworkbook -WorkbookName:SM_Live.xls -Server:S1  
```  
  
## <a name="see-also"></a>請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)