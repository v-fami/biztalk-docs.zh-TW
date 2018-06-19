---
title: 如何使用追蹤公用程式中主控件初始化的 SSO |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- host initiated SSO, trace utility
- trace utility
ms.assetid: a53444d1-3f63-42a6-8ee6-b60ff9af9e41
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebb2003cc6091e3f14bd863902e03649d9005722
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973452"
---
# <a name="how-to-use-the-trace-utility-in-host-initiated-sso"></a><span data-ttu-id="c6e3d-102">如何使用追蹤公用程式中主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="c6e3d-102">How to Use the Trace Utility in Host Initiated SSO</span></span>
<span data-ttu-id="c6e3d-103">疑難排解的主要方法是追蹤。</span><span class="sxs-lookup"><span data-stu-id="c6e3d-103">The primary method of troubleshooting is tracing.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="c6e3d-104">追蹤</span><span class="sxs-lookup"><span data-stu-id="c6e3d-104">Tracing</span></span>  
 <span data-ttu-id="c6e3d-105">使用「追蹤」命令列公用程式在 SSO 中啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="c6e3d-105">Use the Trace command line utility to enable tracing in SSO.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6e3d-106">若要讓追蹤命令發揮效用，tracelog.exe 檔案必須位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="c6e3d-106">For the trace command to function, the file tracelog.exe must be in the following directory:</span></span>  
>   
>  <span data-ttu-id="c6e3d-107">\<*磁碟機*\>: Files\Enterprise Single Sign-on \Program Files\Common</span><span class="sxs-lookup"><span data-stu-id="c6e3d-107">\<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6e3d-108">您可以從下列位置下載這個檔案： [http://go.microsoft.com/fwlink/?LinkId=59534](http://go.microsoft.com/fwlink/?LinkId=59534)</span><span class="sxs-lookup"><span data-stu-id="c6e3d-108">You can download this file from the following location: [http://go.microsoft.com/fwlink/?LinkId=59534](http://go.microsoft.com/fwlink/?LinkId=59534)</span></span>  
  
#### <a name="to-use-the-trace-utility"></a><span data-ttu-id="c6e3d-109">使用追蹤公用程式</span><span class="sxs-lookup"><span data-stu-id="c6e3d-109">To use the trace utility</span></span>  
  
1.  <span data-ttu-id="c6e3d-110">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="c6e3d-110">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="c6e3d-111">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="c6e3d-111">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="c6e3d-112">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="c6e3d-112">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="c6e3d-113">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="c6e3d-113">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="c6e3d-114">型別**Trace – start – high**將追蹤層級設定為高，並開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="c6e3d-114">Type **Trace –start –high** to set the tracing level to high and begin the trace.</span></span>  
  
5.  <span data-ttu-id="c6e3d-115">執行主控件初始化的 SSO 的實例。</span><span class="sxs-lookup"><span data-stu-id="c6e3d-115">Run the scenario with host initiated SSO.</span></span>  
  
6.  <span data-ttu-id="c6e3d-116">型別**Trace – 停止**以結束追蹤。</span><span class="sxs-lookup"><span data-stu-id="c6e3d-116">Type **Trace –stop** to end the trace.</span></span> <span data-ttu-id="c6e3d-117">會在上述目錄中產生一個 .bin 檔案，您可以將該檔案傳送至 Microsoft 進行分析。</span><span class="sxs-lookup"><span data-stu-id="c6e3d-117">A .bin file is generated in the directory above, which you can send to Microsoft for analysis.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6e3d-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="c6e3d-118">See Also</span></span>  
 [<span data-ttu-id="c6e3d-119">主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="c6e3d-119">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)