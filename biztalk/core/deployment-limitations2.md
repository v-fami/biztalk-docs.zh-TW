---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 314bffd50e152c1e3141e4f644c60bdbe7a3824a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011031"
---
# <a name="deployment-limitations"></a><span data-ttu-id="67164-101">部署限制</span><span class="sxs-lookup"><span data-stu-id="67164-101">Deployment Limitations</span></span>
<span data-ttu-id="67164-102">傳輸配接器 」 密碼會儲存為星號 (\*\*\*\*\*\*) 中的繫結檔案匯出 BizTalk 部署精靈 」，並傳遞給管理在相同的格式中的元件。</span><span class="sxs-lookup"><span data-stu-id="67164-102">The Transport Adapter password is stored as asterisks (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Deployment Wizard, and is passed to the management component in the same format.</span></span> <span data-ttu-id="67164-103">繫結檔案前先行編輯匯入的星號取代成隨機英數字元值 （也就是不正確的密碼）。</span><span class="sxs-lookup"><span data-stu-id="67164-103">Edit the binding file before importing by replacing the asterisks with random alphanumeric values (that is, not the correct password).</span></span> <span data-ttu-id="67164-104">然後輸入正確的密碼使用**傳輸屬性**匯入繫結檔案後的頁面。</span><span class="sxs-lookup"><span data-stu-id="67164-104">Then enter the correct password using the **Transport Properties** page after importing the binding file.</span></span>  
  
 <span data-ttu-id="67164-105">當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。</span><span class="sxs-lookup"><span data-stu-id="67164-105">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="67164-106">這可防止密碼資訊以純文字方式出現。</span><span class="sxs-lookup"><span data-stu-id="67164-106">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="67164-107">下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="67164-107">The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="67164-108">或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="67164-108">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="67164-109">在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。</span><span class="sxs-lookup"><span data-stu-id="67164-109">In this case, you must delete the passwords from the binding file after the import operation successfully completes.</span></span>  
  

## <a name="password-limitation-workaround"></a><span data-ttu-id="67164-110">密碼限制解決方法</span><span class="sxs-lookup"><span data-stu-id="67164-110">Password Limitation Workaround</span></span>  
 <span data-ttu-id="67164-111">作為下列其中一種解決密碼限制問題。</span><span class="sxs-lookup"><span data-stu-id="67164-111">Use one of the following as a work-around for the password limitation.</span></span>  
  
#### <a name="to-work-around-the-password-limitation"></a><span data-ttu-id="67164-112">解決密碼限制問題</span><span class="sxs-lookup"><span data-stu-id="67164-112">To work around the password limitation</span></span>  
  
1. <span data-ttu-id="67164-113">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為純文字。</span><span class="sxs-lookup"><span data-stu-id="67164-113">Edit the binding file before importing by replacing the stars with plain text.</span></span>  
  
   > [!CAUTION]
   >  <span data-ttu-id="67164-114">基於安全理由，並不建議使用這個做法。</span><span class="sxs-lookup"><span data-stu-id="67164-114">This is not recommended for security reasons.</span></span>  
  
2. <span data-ttu-id="67164-115">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。</span><span class="sxs-lookup"><span data-stu-id="67164-115">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="67164-116">輸入正確的密碼使用**傳輸屬性**匯入繫結檔案後的頁面。</span><span class="sxs-lookup"><span data-stu-id="67164-116">Enter the correct password using the **Transport Properties** page after importing the binding file.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="67164-117">只有當目標電腦上安裝了 Microsoft Visual Studio，或您開發自訂工具時，才能使用這項解決方法。</span><span class="sxs-lookup"><span data-stu-id="67164-117">This work-around can be used only if Microsoft Visual Studio is installed on the target computer or by developing a custom tool.</span></span>  
  
   <span data-ttu-id="67164-118">**-或-**</span><span class="sxs-lookup"><span data-stu-id="67164-118">**-OR-**</span></span>  
  
#### <a name="to-work-around-the-password-limitation"></a><span data-ttu-id="67164-119">解決密碼限制問題</span><span class="sxs-lookup"><span data-stu-id="67164-119">To work around the password limitation</span></span>  
  
1.  <span data-ttu-id="67164-120">不使用密碼，改為使用「企業單一登入」。</span><span class="sxs-lookup"><span data-stu-id="67164-120">Use Enterprise Single Sign-On instead of using passwords.</span></span>  
  
     <span data-ttu-id="67164-121">使用 SSO 選項只需要先匯入繫結檔案，不需要額外操作。</span><span class="sxs-lookup"><span data-stu-id="67164-121">Using the SSO option requires no extra work; only an import of the binding file.</span></span>  
  
2.  <span data-ttu-id="67164-122">驗證邏輯系統以及「傳輸」和「接收」服務。</span><span class="sxs-lookup"><span data-stu-id="67164-122">Verify the Logical system and the Transmit and Receive services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67164-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67164-123">See Also</span></span>  
 <span data-ttu-id="67164-124">[將成品新增至 BizTalk 管理](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span><span class="sxs-lookup"><span data-stu-id="67164-124">[Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span></span>  
 [<span data-ttu-id="67164-125">匯入 JD Edwards OneWorld 應用程式</span><span class="sxs-lookup"><span data-stu-id="67164-125">Import the JD Edwards OneWorld app</span></span>](deploying-biztalk-adapter-for-jd-edwards-oneworld.md)