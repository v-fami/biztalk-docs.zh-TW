---
title: 外部處理提交使用自訂處理常式的例外狀況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fa661e-d391-47c0-92d5-1d0c45b5963d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ba3fc49756619f77188f0a311ff46eb18e7f0b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294054"
---
# <a name="handling-externally-submitted-exceptions-using-a-custom-handler"></a><span data-ttu-id="c320b-102">外部處理提交使用自訂處理常式的例外狀況</span><span class="sxs-lookup"><span data-stu-id="c320b-102">Handling Externally Submitted Exceptions Using a Custom Handler</span></span>
<span data-ttu-id="c320b-103">在此使用情況下，外部用戶端送出透過 Web 服務例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="c320b-103">In this use case, an external client submits an exception message through a Web service.</span></span> <span data-ttu-id="c320b-104">傳送埠，以 ESB 例外狀況編碼器管線元件，預先設定訂閱的錯誤訊息。它會處理並將它保存為磁碟檔案，您可以使用檢視 Microsoft InfoPath 中圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="c320b-104">A send port, preconfigured with the ESB Exception Encoder pipeline component, subscribes to the fault message; it processes and persists it as a disk file that you can view using Microsoft InfoPath, as shown in Figure 1.</span></span>  
  
 <span data-ttu-id="c320b-105">![處理外部例外狀況](../esb-toolkit/media/ch3-handlingexternalexceptions.gif "Ch3 HandlingExternalExceptions")</span><span class="sxs-lookup"><span data-stu-id="c320b-105">![Handling External Exceptions](../esb-toolkit/media/ch3-handlingexternalexceptions.gif "Ch3-HandlingExternalExceptions")</span></span>  
  
 <span data-ttu-id="c320b-106">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="c320b-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="c320b-107">**處理內送的例外狀況或錯誤訊息，並將保存到磁碟檔案**</span><span class="sxs-lookup"><span data-stu-id="c320b-107">**Handling incoming exception or fault messages and persisting to a disk file**</span></span>  
  
 <span data-ttu-id="c320b-108">「 例外狀況處理服務 」 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。</span><span class="sxs-lookup"><span data-stu-id="c320b-108">The Exception Handling Service Sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="c320b-109">它示範如何使用 ESB 例外狀況服務做為通用的機制，來提交錯誤訊息，從外部應用程式，將會儲存在[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]例外狀況管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="c320b-109">It shows how to use the ESB Exception Service as a universal mechanism to submit fault messages from external applications that will be stored in the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exception management database.</span></span> <span data-ttu-id="c320b-110">如需詳細資訊，請參閱[執行例外狀況處理服務範例](../esb-toolkit/running-the-exception-handling-service-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="c320b-110">For more information, see [Running the Exception Handling Service Sample](../esb-toolkit/running-the-exception-handling-service-sample.md).</span></span>