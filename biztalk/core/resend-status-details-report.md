---
title: 重新傳送狀態詳細資料報表 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3cbc9d44-9a9a-4272-a138-ebd126a9f809
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2335b10da205258f32a6676a6fee2a3ff32fef65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268414"
---
# <a name="resend-status-details-report"></a><span data-ttu-id="1e486-102">重新傳送狀態詳細資料報表</span><span class="sxs-lookup"><span data-stu-id="1e486-102">Resend Status Details Report</span></span>
<span data-ttu-id="1e486-103">此狀態報表嘗試重試合作對象當做 AS2 接收者的合作對象屬性設定為重新傳送 AS2 訊息，如果未收到 MDN 時顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="1e486-103">This status report displays information on retry attempts made when the Party as AS2 Receiver properties of a party are configured to resend the AS2 message if an MDN is not received.</span></span>  
  
 <span data-ttu-id="1e486-104">這個報表顯示 [AS2/MDN 狀態] 報告中的訊息上按一下滑鼠右鍵，然後按一下**檢視可靠傳訊狀態**。</span><span class="sxs-lookup"><span data-stu-id="1e486-104">You display this report by right-clicking on a message in the AS2/MDN status report, and then clicking **View Reliable Messaging Status**.</span></span> <span data-ttu-id="1e486-105">重新傳送狀態詳細資料頁面會再顯示此訊息重新傳送嘗試資訊。</span><span class="sxs-lookup"><span data-stu-id="1e486-105">The Resend Status Details page will then display information on the resend attempts made for this message.</span></span>  
  
 <span data-ttu-id="1e486-106">此報表才可使用您已選取**重新傳送 AS2 訊息，若未收到 MDN**的合作對象做為相關合作對象的 AS2 訊息接收者屬性。</span><span class="sxs-lookup"><span data-stu-id="1e486-106">This report is only available if you have selected **Resend AS2 message if MDN not received** in the Party as AS2 Message Receiver properties for the related party.</span></span>  
  
 <span data-ttu-id="1e486-107">報表會顯示在下列頁面上的訊息重試次數的資訊：</span><span class="sxs-lookup"><span data-stu-id="1e486-107">The report displays information on the retry attempts made for the message on the following pages:</span></span>  
  
|<span data-ttu-id="1e486-108">頁面</span><span class="sxs-lookup"><span data-stu-id="1e486-108">Page</span></span>|<span data-ttu-id="1e486-109">顯示資料</span><span class="sxs-lookup"><span data-stu-id="1e486-109">Data Displayed</span></span>|  
|----------|--------------------|  
|<span data-ttu-id="1e486-110">**一般**</span><span class="sxs-lookup"><span data-stu-id="1e486-110">**General**</span></span>|<span data-ttu-id="1e486-111">目前傳送嘗試，以及重新傳送組態的索引。</span><span class="sxs-lookup"><span data-stu-id="1e486-111">The index of the current send attempt as well as the resend configuration.</span></span>|  
|<span data-ttu-id="1e486-112">**重新傳送歷程記錄**</span><span class="sxs-lookup"><span data-stu-id="1e486-112">**Resend History**</span></span>|<span data-ttu-id="1e486-113">訊息的傳送嘗試的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="1e486-113">A history of send attempts for the message.</span></span>|