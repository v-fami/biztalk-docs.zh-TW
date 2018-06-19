---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-tibco-enterprise-message-service/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: b669c06c5c474d5ce134b593dcecd110c6e8d572
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015717"
---
# <a name="deployment-limitations"></a>部署限制
「 傳輸配接器 」 密碼儲存為顆星 (\*\*\*\*\*\*) 繫結檔案中，會匯出 BizTalk Server 中，並且會傳遞給在同一個管理元件格式。 在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。 輸入正確的密碼使用**傳輸屬性**在 BizTalk Server 管理主控台，在匯入繫結檔案之後的頁面。  
  
 此為已知的限制狀況。 當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。 這可防止密碼資訊以純文字方式出現。 下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。 或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。 在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。  
  
  
## <a name="password-limitation-workaround"></a>密碼限制解決方法  
 若要解決這項密碼限制問題，請使用下列其中一個方法：  
  
-   在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為純文字。  
  
> [!CAUTION]
>  基於安全理由，並不建議使用這個做法。  
  
-   在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。 輸入正確的密碼使用**傳輸屬性**在 BizTalk Server 管理主控台，在匯入繫結檔案之後的頁面。  
  
> [!NOTE]
>  只有當目標電腦上安裝了 Visual Studio，或您開發自訂工具時，才能使用這項解決方法。  
  
-   驗證邏輯系統以及「傳輸」和「接收」服務。  
  
