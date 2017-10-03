---
title: "分割 HIPAA 子文件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66d9badd-00c6-43a3-807e-0ad313983adc
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 799cb5813b3c13339a0c477bf142a467a91b2c94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="splitting-hipaa-subdocuments"></a>分割 HIPAA 子文件
HIPAA 的 EDI 交換通常會在單一交易集中，使用由 ST/SE 標頭繫結的多重子 (child/sub) 文件。 EDI 接收管線，可支援從該等交易集建立不同的 HIPAA 子文件。 這種方式不同於「非 HIPAA EDI 交換」將單一交易集當作單一訊息來處理的方式。  
  
## <a name="subdocument-splitting-schemas"></a>子文件分割結構描述  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援透過原生結構描述分割下列 HIPAA 文件類型：  
  
-   HIPAA 4010 版文件： 834 Enrollment、 835 Claim Payment 與 837 Claim 的三種變化  
  
-   HIPAA 5010 版文件： 276/277 Claim Status – 要求與回應、 834 Enrollment 與 837 Claim 的三種變化  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會針對上述三種文件類型分別提供兩種版本的結構描述。 對於每一種文件類型，支援分割的結構描述檔名會用 ‘Multiple’ 標記提供識別。 其他的結構描述則不支援子文件分割。  
  
 有些實例可能同時需要使用分割和非分割類型的結構描述。 藉由針對其中一個結構描述的變化使用自訂的目標命名空間，就可以同時使用兩種結構描述。  
  
## <a name="how-subdocument-splitting-is-enabled"></a>分割子文件的啟用方式  
 分割 HIPAA 子文件的功能，是透過 HIPAA 結構描述中的三個註解項目啟用。 前兩個是在應用程式資訊註解，必須設定為結構描述的項目**是**:  
  
```  
subdocument_break = "yes" Split_Without_Sibling_Data = "Yes"  
```  
  
 第三個註解項目位在 HIPAA 結構描述內的適當記錄層級上。 這個屬性也必須設定為**是**。  
  
```  
subdocument_creation_break = "yes"  
```  
  
 只有在 HIPAA 結構描述中的子文件建立分頁註解是設為 "Yes"，以及「輸入批次處理選項」的合作對象屬性是設為「將交換分割為交易集」時，HIPAA 交換才會分割成子文件。 如果輸入批次處理選項的合作對象屬性是設為「保留交換」，EDI 解譯器就不會將該交換成子文件。 在這種情況下，EDI 解譯器將會忽略該註解。 發生這種情況時，事件檢視器中並不會發出任何警告。  
  
> [!NOTE]
>  子文件建立分頁註解不能為巢狀。 如果結構描述包含有套用子文件註解的迴圈，該迴圈一定不能包含另一個有套用子文件註解的迴圈。  
  
## <a name="how-subdocuments-are-processed"></a>子文件的處理方式  
 EDI 接收管線中的 EDI 解譯器會分割子文件。 在接收管線驗證內送交換並產生適當的應答後，它會將各個子文件路由到 MessageBox。 每份子文件在結構上和語法上都是正確的；不過，商務層級摘要、交易集總計和交易集控制編號應該還沒執行同步處理。 傳送管線會將每份子文件之 SE01 中的現有區段計數 (來自原始的交易集)，覆寫成子文件中已包含區段的計數。 接收管線會同時重設每份子文件中的交易集控制編號，這樣該子文件就不會出現重複的控制編號。 這樣可確保傳送端處理不會失敗。  
  
 如果交易集在子文件分割期間未成功執行 EDI 或接續的驗證作業，每個失敗的交易集將進入擱置狀態。  
  
 訂閱這些子文件的傳送埠將從 MessageBox 接收每份子文件，序列化這些 XML 子文件，批次處理它們 (在啟用情況下)，驗證它們，然後傳送它們。 傳送管線會更新區段資料項目 (SE01) 的計數。  
  
## <a name="how-subdocuments-are-split"></a>子文件的分割方式  
 子文件建立分頁註解，通常會套用到包含有 HIPAA 結構描述中一或多個項目的迴圈。 在結構描述中該分頁迴圈前後的其他項目，則會複製到各個多重子文件中。  
  
 下表列出子文件分割範例。 在這個範例中，CC 項目迴圈的子文件建立分頁註解是設成 "Yes"。 這樣一來，在交易集中的 CC 項目會分割成不同的子文件，而該交易集內的 AA、BB 和 DD 項目，則會完整包括到個別子文件中。  
  
|結構描述 (最小和最大相符項目)|原始執行個體|子文件 #1|子文件 #2|子文件 #3|  
|---------------------------------------|-----------------------|---------------------|---------------------|---------------------|  
|ST (1,0)|ST|ST|ST|ST|  
|AA (1,1)|AA|AA|AA|AA|  
|BB loop (1,n)<br /><br /> BB1 (1,n)<br /><br /> CC loop (1,n) - subdocument_break = "yes"<br /><br /> CC1 (1,n)<br /><br /> CC2 (0,n)<br /><br /> BB2 (0,n)|BB1*1<br /><br /> CC1\*1<br /><br /> CC2\*1<br /><br /> BB2\*1<br /><br /> BB1\*2<br /><br /> CC1\*2<br /><br /> CC2\*2<br /><br /> BB1\*3<br /><br /> CC1\*3<br /><br /> CC2\*3|BB1*1<br /><br /> CC1\*1<br /><br /> CC2\*1<br /><br /> BB2\*1|BB1*2<br /><br /> CC1\*2<br /><br /> CC2\*2|BB1*3<br /><br /> CC1\*3<br /><br /> CC2\*3|  
|DD (0,n)|DD|DD|DD|DD|  
|SE|SE|SE|SE|SE|