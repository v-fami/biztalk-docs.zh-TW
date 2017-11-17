---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 847e66c189cb8fc14014691f95d78b6eec4b45dc
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="deployment-limitations"></a><span data-ttu-id="da580-101">部署限制</span><span class="sxs-lookup"><span data-stu-id="da580-101">Deployment Limitations</span></span>
<span data-ttu-id="da580-102">「傳輸配接器」密碼以星號 (******) 儲存在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 匯出的繫結檔案中，並且會以相同格式傳遞給管理元件。</span><span class="sxs-lookup"><span data-stu-id="da580-102">The Transport Adapter password is stored as stars (******) in the binding file that is exported by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format.</span></span> <span data-ttu-id="da580-103">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。</span><span class="sxs-lookup"><span data-stu-id="da580-103">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span>  
  
 <span data-ttu-id="da580-104">當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。</span><span class="sxs-lookup"><span data-stu-id="da580-104">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="da580-105">這可防止密碼資訊以純文字方式出現。</span><span class="sxs-lookup"><span data-stu-id="da580-105">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="da580-106">下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="da580-106">The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span>  
  
 <span data-ttu-id="da580-107">或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="da580-107">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="da580-108">在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。</span><span class="sxs-lookup"><span data-stu-id="da580-108">In this case, you must delete the passwords from the binding file after the import operation successfully completes.</span></span>  
  
## <a name="password-limitation-workaround"></a><span data-ttu-id="da580-109">密碼限制解決方法</span><span class="sxs-lookup"><span data-stu-id="da580-109">Password Limitation Workaround</span></span>  
 <span data-ttu-id="da580-110">若要解決密碼限制問題，您可以執行下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="da580-110">To work around the password limitation, you can do the following.</span></span>  
  
#### <a name="to-work-around-the-password-limitation"></a><span data-ttu-id="da580-111">解決密碼限制問題</span><span class="sxs-lookup"><span data-stu-id="da580-111">To work around the password limitation</span></span>  
  
1.  <span data-ttu-id="da580-112">不使用密碼，改為使用「企業單一登入」。</span><span class="sxs-lookup"><span data-stu-id="da580-112">Use Enterprise Single Sign-On instead of using passwords.</span></span> <span data-ttu-id="da580-113">使用 SSO 選項只需要先匯入繫結檔案，不需要額外操作。</span><span class="sxs-lookup"><span data-stu-id="da580-113">Using the SSO option requires no extra work; only an import of the binding file.</span></span>  
  
2.  <span data-ttu-id="da580-114">驗證邏輯系統以及「傳輸」和「接收」服務。</span><span class="sxs-lookup"><span data-stu-id="da580-114">Verify the Logical system and the Transmit and Receive services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da580-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da580-115">See Also</span></span>  
 [<span data-ttu-id="da580-116">匯入 JD Edwards EnterpriseOne 應用程式</span><span class="sxs-lookup"><span data-stu-id="da580-116">Import the JD Edwards EnterpriseOne app</span></span>](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md)