---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-peoplesoft-enterprise/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 9d12874ef6042580183f407afc811a9d7f6e0fc9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009863"
---
# <a name="deployment-limitations"></a><span data-ttu-id="aebec-101">部署限制</span><span class="sxs-lookup"><span data-stu-id="aebec-101">Deployment Limitations</span></span>

## <a name="overview"></a><span data-ttu-id="aebec-102">概觀</span><span class="sxs-lookup"><span data-stu-id="aebec-102">Overview</span></span>
<span data-ttu-id="aebec-103">「傳輸配接器」密碼以星號 (******) 儲存在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 匯出的繫結檔案中，並且會以相同格式傳遞給管理元件。</span><span class="sxs-lookup"><span data-stu-id="aebec-103">The Transport Adapter password is stored as stars (******) in the binding file that is exported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format.</span></span>  
  
 <span data-ttu-id="aebec-104">當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。</span><span class="sxs-lookup"><span data-stu-id="aebec-104">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="aebec-105">這可防止密碼資訊以純文字方式出現。</span><span class="sxs-lookup"><span data-stu-id="aebec-105">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="aebec-106">下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="aebec-106">The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="aebec-107">或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="aebec-107">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="aebec-108">在這種情況下，匯入作業完成後您必須刪除繫結檔案中的密碼。</span><span class="sxs-lookup"><span data-stu-id="aebec-108">In this case, you must delete the passwords from the binding file after the import operation finishes.</span></span>  
  

## <a name="password-limitation-workaround"></a><span data-ttu-id="aebec-109">密碼限制解決方法</span><span class="sxs-lookup"><span data-stu-id="aebec-109">Password Limitation Workaround</span></span>  
 <span data-ttu-id="aebec-110">若要解決這項密碼限制問題，請使用下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="aebec-110">To work around this password limitation, you can use one of the following methods:</span></span>  
  
- <span data-ttu-id="aebec-111">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為純文字。</span><span class="sxs-lookup"><span data-stu-id="aebec-111">Edit the binding file before importing by replacing the stars with plain text.</span></span>  
  
  > [!CAUTION]
  >  <span data-ttu-id="aebec-112">基於安全性理由，並不建議使用這個做法。</span><span class="sxs-lookup"><span data-stu-id="aebec-112">This practice is not recommended for security reasons.</span></span>  
  
- <span data-ttu-id="aebec-113">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。</span><span class="sxs-lookup"><span data-stu-id="aebec-113">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="aebec-114">輸入正確的密碼使用**傳輸屬性**在 BizTalk Server 管理主控台，匯入繫結檔案後的頁面。</span><span class="sxs-lookup"><span data-stu-id="aebec-114">Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="aebec-115">只有當目標電腦上安裝了 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，或您開發自訂工具時，才能使用這項解決方法。</span><span class="sxs-lookup"><span data-stu-id="aebec-115">This work-around can be used only if Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] is installed on the target computer, or if you develop a custom tool.</span></span>  
  
  <span data-ttu-id="aebec-116">-或-</span><span class="sxs-lookup"><span data-stu-id="aebec-116">-or-</span></span>  
  
- <span data-ttu-id="aebec-117">不使用密碼，改為使用「企業單一登入」(SSO)。</span><span class="sxs-lookup"><span data-stu-id="aebec-117">Use Enterprise Single Sign-On (SSO) instead of using passwords.</span></span>  
  
   <span data-ttu-id="aebec-118">使用 SSO 選項需要先匯入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="aebec-118">Using the SSO option requires an import of the binding file.</span></span>  
  
  <span data-ttu-id="aebec-119">驗證邏輯系統以及「傳輸」和「接收」服務。</span><span class="sxs-lookup"><span data-stu-id="aebec-119">Verify the logical system and the Transmit and Receive services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aebec-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aebec-120">See Also</span></span>  
[<span data-ttu-id="aebec-121">匯入繫結與限制</span><span class="sxs-lookup"><span data-stu-id="aebec-121">Import bindings & limitations</span></span>](../core/deploying-biztalk-adapter-for-peoplesoft-enterprise.md)