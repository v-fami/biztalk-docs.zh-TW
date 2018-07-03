---
title: 最佳做法來管理 Certificates2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71fa00cc-2e0c-46b3-ae62-f130a5b5f4f5
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e2b79e2a0d7e4758ac87503f4bfac122c9ee215
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994783"
---
# <a name="best-practices-for-managing-certificates"></a>管理憑證的最佳作法
本節提供在您的 Microsoft BizTalk Server 環境中管理憑證的最佳作法。  
  
## <a name="assess-and-plan-your-use-of-certificates"></a>評估及規劃您使用的憑證  
 **執行環境的威脅模型分析**  
  
- 執行您環境的「威脅模型分析」(TMA) 以判斷簽章或加密憑證是否有助於減輕安全性威脅。  
  
  **建立與夥伴的公開金鑰憑證的計劃**  
  
- 建立將公開金鑰憑證來傳送和接收來自夥伴的公開金鑰憑證的計劃。 如果您沒有使用簽章憑證進行合作對象解析，則可以將公用憑證附加到訊息；在此情況下，您的系統並不需要預先準備憑證的複本。  
  
  **與合作夥伴的指導方針建立提交公開金鑰**  
  
- 在與夥伴的「服務等級協議」(SLA) 內容中，建立提交公開金鑰的指導方針，在他們的憑證即將到期時，以及在他們撤銷憑證時通知您。  
  
## <a name="install-certificates"></a>安裝憑證  
 **設定的間隔下載憑證撤銷清單**  
  
- 下載從您的憑證授權單位 (CA) 憑證撤銷清單 (CRL) 設定的間隔。 我們建議一週下載一次。 如果 BizTalk 伺服器所加入的網域有 CA 存在，便會自動下載 CRL。  
  
  **驗證簽章憑證**  
  
- 您務必要根據憑證撤銷清單驗證簽章憑證。 如需如何驗證簽章憑證的詳細資訊，請參閱[如何設定 MIME/SMIME 解碼器管線元件](http://go.microsoft.com/fwlink/?LinkId=155145)(<http://go.microsoft.com/fwlink/?LinkId=155145>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
  **管理憑證與合作夥伴**  
  
- 將憑證管理納入夥伴管理實務的環節。 在從 BizTalk Server 環境中新增或移除合作對象時，建議您新增或移除與該夥伴相關聯的憑證。  
  
  **移除主控件執行個體前移除憑證**  
  
- 從 BizTalk Server 移除主控件執行個體前，請先移除主控件執行個體執行時所用帳戶的個人存放區中的憑證。  
  
## <a name="configure-biztalk-server-to-use-certificates-for-mimesmime"></a>設定 BizTalk Server 使用 MIME/SMIME 憑證  
 **避免阻斷服務攻擊，數位簽章**  
  
- 決定您想要的郵件，當 BizTalk Server 無法驗證數位簽章。 設定接收埠上的 [驗證] 屬性，有助於防止阻絕服務攻擊。  
  
  > [!NOTE]
  >  驗證-捨棄訊息並驗證-保留訊息的接收埠上的旗標需要正確地設定 「 合作對象解析 」 管線元件和合作對象 BizTalk Server 中定義。 如需詳細資訊，請參閱 <<c0> [ 合作對象解析管線元件](http://go.microsoft.com/fwlink/?LinkId=155146)(<http://go.microsoft.com/fwlink/?LinkId=155146>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
  **建立個別的加密和未加密的訊息接收位置**  
  
- 如果您打算從某些夥伴接收 MIME 加密訊息，並從其他夥伴接收未加密的訊息，請在不同的主控件中，為加密和未加密的訊息分別建立接收位置。 當您預期只有 MIME 加密訊息時的 [允許非 MIME 訊息] 選項則會在解碼 MIME/SMIME 管線元件，為 [否] 中設定  
  
## <a name="configure-a-biztalk-adapter-to-use-certificates"></a>設定 BizTalk 配接器使用的憑證  
 **測試目標網站的連接**  
  
- 如果您使用 SSL，請確定您可以連接到目標網站，使用 Microsoft Internet Explorer® 再嘗試連線到目標網站，使用 HTTP 或 SOAP 傳輸。 請確認當您連接到目標網站時，會在 Internet Explorer 中顯示任何對話方塊。 BizTalk Server 並沒有任何機制互動與連接到目標網站時，可能會顯示任何對話方塊。 如果目標網站名稱不符合指定 SSL 憑證中網站的名稱，或針對 SSL 憑證的根憑證授權單位不是適當的信任根憑證，可能會由 Internet Explorer 顯示對話方塊授權單位存放區。  
  
  **使用 SSL 診斷工具分析 SSL 連接問題**  
  
- SSL 診斷工具是 IIS Diagnostics Toolkit 的一個選用元件。 您可以下載 IIS Diagnostics Toolkit，從[Internet Information Services 診斷工具](http://go.microsoft.com/fwlink/?LinkID=64426)網頁 (http://go.microsoft.com/fwlink/?LinkID=64426)。  
  
## <a name="exporting-a-certificate-from-one-biztalk-group-to-another"></a>將憑證從一個 BizTalk 群組匯出到另一個  
 **確定匯入的憑證使用針對其預定用途**  
  
-   如果您匯入到群組中的憑證，匯入的憑證必須符合其預期用途的使用方式屬性。 若要查看使用方式 屬性，連按兩下中的憑證**憑證管理主控台**介面，然後按一下**詳細資料**索引標籤**憑證** 對話方塊。 然後按一下**所有**選項**顯示**下拉式清單，然後按一下以選取**金鑰使用方法**及/或**增強金鑰使用方法**欄位若要確認預定的目的。 如果 BizTalk Server 會嘗試使用其預定用途以外的憑證會發生執行階段錯誤。