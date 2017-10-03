---
title: "部署 Limitations2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deployment, limitations
- passwords, adapter limitations
ms.assetid: 9db2ca70-5db2-4b14-a898-13049737c188
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05fa9704823bd7e9df9f0bc7d4516719a8a490e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deployment-limitations"></a><span data-ttu-id="20de3-102">部署限制</span><span class="sxs-lookup"><span data-stu-id="20de3-102">Deployment Limitations</span></span>
<span data-ttu-id="20de3-103">傳輸配接器 」 密碼會儲存為星號 (\*\*\*\*\*\*) 中繫結檔案匯出 BizTalk 部署精靈 」，並傳遞給管理以相同格式的元件。</span><span class="sxs-lookup"><span data-stu-id="20de3-103">The Transport Adapter password is stored as asterisks (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Deployment Wizard, and is passed to the management component in the same format.</span></span> <span data-ttu-id="20de3-104">匯入星號取代成隨機英數字元值 （也就是不正確的密碼） 之前編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="20de3-104">Edit the binding file before importing by replacing the asterisks with random alphanumeric values (that is, not the correct password).</span></span> <span data-ttu-id="20de3-105">然後輸入正確的密碼使用**傳輸屬性**匯入繫結檔案後的頁面。</span><span class="sxs-lookup"><span data-stu-id="20de3-105">Then enter the correct password using the **Transport Properties** page after importing the binding file.</span></span>  
  
 <span data-ttu-id="20de3-106">當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。</span><span class="sxs-lookup"><span data-stu-id="20de3-106">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="20de3-107">這可防止密碼資訊以純文字方式出現。</span><span class="sxs-lookup"><span data-stu-id="20de3-107">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="20de3-108">下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="20de3-108">The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="20de3-109">或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="20de3-109">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="20de3-110">在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。</span><span class="sxs-lookup"><span data-stu-id="20de3-110">In this case, you must delete the passwords from the binding file after the import operation successfully completes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20de3-111">匯入到.msi 檔案時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包含企業配接器之繫結資訊的應用程式可能會收到匯入錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="20de3-111">When importing an .msi file into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application containing binding information for any of the Enterprise adapters, you may receive an import error message.</span></span> <span data-ttu-id="20de3-112">支援的 hotfix 可從 Microsoft 以及在錯誤的完整說明[http://support.microsoft.com/kb/923733/en-us](http://support.microsoft.com/kb/923733/en-us)。</span><span class="sxs-lookup"><span data-stu-id="20de3-112">A supported hotfix is available from Microsoft along with a full description of the error at [http://support.microsoft.com/kb/923733/en-us](http://support.microsoft.com/kb/923733/en-us).</span></span>  
  
## <a name="password-limitation-workaround"></a><span data-ttu-id="20de3-113">密碼限制解決方法</span><span class="sxs-lookup"><span data-stu-id="20de3-113">Password Limitation Workaround</span></span>  
 <span data-ttu-id="20de3-114">使用下列其中一種解決方法的密碼限制問題。</span><span class="sxs-lookup"><span data-stu-id="20de3-114">Use one of the following as a work-around for the password limitation.</span></span>  
  
#### <a name="to-work-around-the-password-limitation"></a><span data-ttu-id="20de3-115">解決密碼限制問題</span><span class="sxs-lookup"><span data-stu-id="20de3-115">To work around the password limitation</span></span>  
  
1.  <span data-ttu-id="20de3-116">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為純文字。</span><span class="sxs-lookup"><span data-stu-id="20de3-116">Edit the binding file before importing by replacing the stars with plain text.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="20de3-117">基於安全理由，並不建議使用這個做法。</span><span class="sxs-lookup"><span data-stu-id="20de3-117">This is not recommended for security reasons.</span></span>  
  
2.  <span data-ttu-id="20de3-118">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。</span><span class="sxs-lookup"><span data-stu-id="20de3-118">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="20de3-119">輸入正確的密碼使用**傳輸屬性**匯入繫結檔案後的頁面。</span><span class="sxs-lookup"><span data-stu-id="20de3-119">Enter the correct password using the **Transport Properties** page after importing the binding file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20de3-120">只有當目標電腦上安裝了 Microsoft Visual Studio，或您開發自訂工具時，才能使用這項解決方法。</span><span class="sxs-lookup"><span data-stu-id="20de3-120">This work-around can be used only if Microsoft Visual Studio is installed on the target computer or by developing a custom tool.</span></span>  
  
 <span data-ttu-id="20de3-121">**-或-**</span><span class="sxs-lookup"><span data-stu-id="20de3-121">**-OR-**</span></span>  
  
#### <a name="to-work-around-the-password-limitation"></a><span data-ttu-id="20de3-122">解決密碼限制問題</span><span class="sxs-lookup"><span data-stu-id="20de3-122">To work around the password limitation</span></span>  
  
1.  <span data-ttu-id="20de3-123">不使用密碼，改為使用「企業單一登入」。</span><span class="sxs-lookup"><span data-stu-id="20de3-123">Use Enterprise Single Sign-On instead of using passwords.</span></span>  
  
     <span data-ttu-id="20de3-124">使用 SSO 選項只需要先匯入繫結檔案，不需要額外操作。</span><span class="sxs-lookup"><span data-stu-id="20de3-124">Using the SSO option requires no extra work; only an import of the binding file.</span></span>  
  
2.  <span data-ttu-id="20de3-125">驗證邏輯系統以及「傳輸」和「接收」服務。</span><span class="sxs-lookup"><span data-stu-id="20de3-125">Verify the Logical system and the Transmit and Receive services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20de3-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20de3-126">See Also</span></span>  
 <span data-ttu-id="20de3-127">[如何設定 JD Edwards OneWorld 傳輸屬性](../core/how-to-set-jd-edwards-oneworld-transport-properties.md) </span><span class="sxs-lookup"><span data-stu-id="20de3-127">[How to Set JD Edwards OneWorld Transport Properties](../core/how-to-set-jd-edwards-oneworld-transport-properties.md) </span></span>  
 [<span data-ttu-id="20de3-128">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="20de3-128">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies4.md)