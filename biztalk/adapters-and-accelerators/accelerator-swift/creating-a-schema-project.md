---
title: "建立結構描述專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67e6278c-a597-4700-80bf-48e37aaa9c05
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58017b24f7b7464745f48cc202734217dfb327d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-schema-project"></a><span data-ttu-id="53175-102">建立結構描述專案</span><span class="sxs-lookup"><span data-stu-id="53175-102">Creating a Schema Project</span></span>
<span data-ttu-id="53175-103">若要建立結構描述專案：</span><span class="sxs-lookup"><span data-stu-id="53175-103">To create a schema project:</span></span>  
  
1.  <span data-ttu-id="53175-104">在 Visual Studio 中建立 SWIFT MX 結構描述的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="53175-104">In Visual Studio, create the SWIFT MX Schema BizTalk project.</span></span>  
  
2.  <span data-ttu-id="53175-105">加入此專案的適當 MX 結構描述 （從 ISO20022 網站下載），您想要測試。</span><span class="sxs-lookup"><span data-stu-id="53175-105">Add the appropriate MX schema (downloaded from ISO20022 site), which you wish to test, to this project.</span></span>  
  
3.  <span data-ttu-id="53175-106">如果您想要執行上述 MX 訊息、 Message Repair 和 New Submission 功能則信封結構描述對應至上述的訊息類型也必須部署其他繼續進行步驟 6。</span><span class="sxs-lookup"><span data-stu-id="53175-106">If you want to execute the Message Repair and New Submission functionality for the above MX message, then an Envelope schema corresponding to the above message type also needs to be deployed else proceed to step 6.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="53175-107">如需如何產生 MX 信封結構描述資訊，請參閱表單產生器文件。</span><span class="sxs-lookup"><span data-stu-id="53175-107">For information on how to generate MX Envelope schemas, please refer to the Form Generator Documentation.</span></span>  
  
4.  <span data-ttu-id="53175-108">SWIFT MX 結構描述專案中加入信封結構描述。</span><span class="sxs-lookup"><span data-stu-id="53175-108">Add the Envelope schema to the SWIFT MX Schema project.</span></span>  
  
5.  <span data-ttu-id="53175-109">在 BizTalk 編輯器中開啟信封結構描述，並將升級"CorrelationToken"和"IsNewSubmission"屬性。</span><span class="sxs-lookup"><span data-stu-id="53175-109">Open the Envelope schema in the BizTalk editor and promote “CorrelationToken” and “IsNewSubmission” properties.</span></span> <span data-ttu-id="53175-110">以滑鼠右鍵按一下上面的欄位，然後按一下**升階]-> [快速升級**來升級這些屬性。</span><span class="sxs-lookup"><span data-stu-id="53175-110">Right-click the above fields and click **Promote -> Quick Promotion** to promote these properties.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="53175-111">如需有關如何升級結構描述屬性的詳細資訊，請參閱 BizTalk Server 文件。</span><span class="sxs-lookup"><span data-stu-id="53175-111">For more information on how to promote properties of a schema, please refer to the BizTalk Server documentation.</span></span>  
  
6.  <span data-ttu-id="53175-112">建立金鑰檔案 （使用 Sn – k key.snk），並將其指派給專案來建立強式名稱組件。</span><span class="sxs-lookup"><span data-stu-id="53175-112">Create a key file (using Sn –k key.snk), and then assign it to the project to create a strong named assembly.</span></span>  
  
7.  <span data-ttu-id="53175-113">建置然後再部署專案。</span><span class="sxs-lookup"><span data-stu-id="53175-113">Build and then deploy the project.</span></span>