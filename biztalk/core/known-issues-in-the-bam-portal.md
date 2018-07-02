---
title: BAM 入口網站的已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e681e910-c664-479c-86f3-a6ae0ec97775
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0533a1431ada4127e2b4746af19b0ccbaf4ecd39
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973071"
---
# <a name="known-issues-in-the-bam-portal"></a>BAM 入口網站中的已知問題
此主題包含協助您辨識和解決在使用 BAM 入口網站時可能會發生的問題。  
  
## <a name="errors-occur-when-the-bam-portal-and-ie-are-on-the-same-computer-and-security-settings-are-low"></a>BAM 入口網站和 IE 位於同一部電腦，且安全性設定為低時，會發生錯誤  
 **問題**  
  
 使用 Internet Explorer 時，您可能會遇到的錯誤訊息**中的伺服器錯誤 ' / BAM' 應用程式**在下列情況下：  
  
- 按一下指向非現有活動執行個體的相關活動。  
  
- 在按一下時**儲存警示**按鈕，在下列案例：  
  
  -   您建立查詢 **[activitysearch]** 頁面，然後按一下**設定警示**。  
  
  -   您完成警示欄位，然後按一下**儲存警示**。  
  
  -   按一下 [上一步] 按鈕。  
  
  -   您按一下**儲存警示**按鈕一次。  
  
  **原因**  
  
  當執行 Internet Explorer 安全性等級設定為低、 Web 要求會以低權限來執行。 為了配合 Windows 整合安全性的問題，Internet Explorer 會通過具有很少權限的使用者 Token。  
  
  如果您是在安裝 BAM 入口網站的同一部電腦上使用 Internet Explorer，而且在 Internet Explorer 中將安全性層級設定為低，則入口網站會模擬具有低權限 Token 的使用者。 這個 Token 沒有事件記錄檔的寫入權限。 入口網站在遇到錯誤時，會嘗試將錯誤記到事件記錄檔，但無法這麼做，因為使用者 Token 降低的權限不足以存取事件記錄檔。  
  
  **解決方式**  
  
  如果您需要從本機電腦瀏覽，您應該加入http://localhost至受信任的站台清單。  
  
#### <a name="add-localhost-to-the-list-of-trusted-sites"></a>新增 localhost 至信任的網站清單  
  
1.  在 Internet Explorer 中，按一下**工具**，然後按一下**網際網路選項**。  
  
2.  按一下 **安全性**索引標籤，然後再按一下**信任的網站**中**選取要檢視或變更安全性設定的區域**視窗。  
  
3.  按一下 [**站台**] 按鈕。  
  
4.  在 **將這個網站新增到區域**文字方塊中，輸入**http://localhost**。 如果**需要伺服器驗證 (https:) 的所有核取方塊**核取方塊，將其清除，然後按一下**新增** 按鈕。 「 網站 」 http://localhost，會出現在**網站**清單。  
  
5.  如有必要，還原**需要伺服器驗證 (https:) 的這個區域中的所有網站**為其原始狀態的核取方塊。  
  
6.  按一下 **關閉**按鈕，然後再按一下**確定**。  
  
## <a name="bam-portal-aggregations-do-not-populate-existing-data-when-using-an-ip-address-as-a-url-in-internet-explorer"></a>Bam 入口網站彙總不會填入現有的資料時使用的 IP 位址為 Internet Explorer 中的 URL
 **問題**  
  
 彙總時使用的 IP 位址做為 URL，使用 Internet Explorer，檢視 BAM 入口網站，顯示下列訊息: 「 沒有詳細資料。 無法處理查詢」。  
  
 **原因**  
  
 在 Internet Explorer 中的預設安全性設定可能會防止存取使用 IPv4 和 IPv6 位址做為 Url 的網站。  
  
 **解決方式**  
  
 將網站位址加入至信任的網站清單，並且啟用存取各網域的資料來源。  
  
#### <a name="add-the-ip-address-to-the-trusted-sites-list"></a>將 IP 位址新增至信任的網站清單  
  
1.  在 Internet Explorer 中，按一下**工具**，然後按一下**網際網路選項**。  
  
2.  按一下 **安全性**索引標籤，然後再按一下**信任的網站**安全性區域。  
  
3.  按一下 [**站台**] 按鈕。  
  
4.  在 **將這個網站新增到區域**，輸入 BAM 入口網站的 IP 位址，然後按一下**新增**。  
  
5.  按一下 [關閉]，然後按一下 [確定]。  
  
#### <a name="enable-access-to-data-sources-across-domains"></a>啟用各網域的資料來源的存取權  
  
1.  在 Internet Explorer 中，按一下**工具**，然後按一下**網際網路選項**。  
  
2.  按一下 **安全性**索引標籤，然後再按一下**信任的網站**安全性區域。  
  
3.  按一下 **自訂層級**按鈕，您向下捲動至**其他**節點**設定**樹狀目錄中。  
  
4.  在 **跨網域存取資料來源**節點中，按一下**啟用選項**按鈕，然後再按一下**確定**。  
  
## <a name="bmexe-does-not-run-in-powershell"></a>BM.exe 未在 PowerShell 中執行  
 **問題**  
  
 下列命令在 PowerShell 中執行時擲出錯誤。  
  
```  
bm.exe get-config -FileName:config.xml  
```  
  
 **原因**  
  
 PowerShell 找不到 .exe 和組態檔的路徑。  
  
 **解決方式**  
  
 如果您在 PowerShell 中使用 bm.exe，請指定 .exe 和組態檔的完整路徑。 例如：`bm.exe get-config -FileName:config.xml`應指定為`“%BizTalkPathTracking%”\bm.exe get-config -FileName:”%InstallDir%”\Tracking\config.xml`。  
  
## <a name="see-also"></a>另請參閱  
 [規劃 BAM 入口網站](../core/planning-for-the-bam-portal.md)