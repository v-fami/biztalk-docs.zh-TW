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
# <a name="deployment-limitations"></a><span data-ttu-id="88a3d-101">部署限制</span><span class="sxs-lookup"><span data-stu-id="88a3d-101">Deployment Limitations</span></span>
<span data-ttu-id="88a3d-102">「 傳輸配接器 」 密碼儲存為顆星 (\*\*\*\*\*\*) 繫結檔案中，會匯出 BizTalk Server 中，並且會傳遞給在同一個管理元件格式。</span><span class="sxs-lookup"><span data-stu-id="88a3d-102">The Transport Adapter password is stored as stars (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Server, and it passes to the management component in the same format.</span></span> <span data-ttu-id="88a3d-103">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。</span><span class="sxs-lookup"><span data-stu-id="88a3d-103">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="88a3d-104">輸入正確的密碼使用**傳輸屬性**在 BizTalk Server 管理主控台，在匯入繫結檔案之後的頁面。</span><span class="sxs-lookup"><span data-stu-id="88a3d-104">Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.</span></span>  
  
 <span data-ttu-id="88a3d-105">此為已知的限制狀況。</span><span class="sxs-lookup"><span data-stu-id="88a3d-105">This is a known limitation.</span></span> <span data-ttu-id="88a3d-106">當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。</span><span class="sxs-lookup"><span data-stu-id="88a3d-106">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="88a3d-107">這可防止密碼資訊以純文字方式出現。</span><span class="sxs-lookup"><span data-stu-id="88a3d-107">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="88a3d-108">下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="88a3d-108">The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="88a3d-109">或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="88a3d-109">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="88a3d-110">在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。</span><span class="sxs-lookup"><span data-stu-id="88a3d-110">In this case, you must delete the passwords from the binding file after the import operation successfully finishes.</span></span>  
  
  
## <a name="password-limitation-workaround"></a><span data-ttu-id="88a3d-111">密碼限制解決方法</span><span class="sxs-lookup"><span data-stu-id="88a3d-111">Password Limitation Workaround</span></span>  
 <span data-ttu-id="88a3d-112">若要解決這項密碼限制問題，請使用下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="88a3d-112">To work around this password limitation, you can use one of the following methods:</span></span>  
  
-   <span data-ttu-id="88a3d-113">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為純文字。</span><span class="sxs-lookup"><span data-stu-id="88a3d-113">Edit the binding file before importing by replacing the stars with plain text.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="88a3d-114">基於安全理由，並不建議使用這個做法。</span><span class="sxs-lookup"><span data-stu-id="88a3d-114">This is not recommended for security reasons.</span></span>  
  
-   <span data-ttu-id="88a3d-115">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。</span><span class="sxs-lookup"><span data-stu-id="88a3d-115">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="88a3d-116">輸入正確的密碼使用**傳輸屬性**在 BizTalk Server 管理主控台，在匯入繫結檔案之後的頁面。</span><span class="sxs-lookup"><span data-stu-id="88a3d-116">Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88a3d-117">只有當目標電腦上安裝了 Visual Studio，或您開發自訂工具時，才能使用這項解決方法。</span><span class="sxs-lookup"><span data-stu-id="88a3d-117">This work-around can be used only if Visual Studio is installed on the target computer, or if you develop a custom tool.</span></span>  
  
-   <span data-ttu-id="88a3d-118">驗證邏輯系統以及「傳輸」和「接收」服務。</span><span class="sxs-lookup"><span data-stu-id="88a3d-118">Verify the Logical system and the Transmit and Receive services.</span></span>  
  
