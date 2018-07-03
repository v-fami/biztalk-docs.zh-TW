---
title: X12 EDI 字元集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76e7b327-b0bd-4f16-8bfe-6c0184059f2b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bd501c81b92f4fa7824009a949fd6c7e58eaf3b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023100"
---
# <a name="x12-edi-character-set"></a><span data-ttu-id="4206b-102">X12 EDI 字元集</span><span class="sxs-lookup"><span data-stu-id="4206b-102">X12 EDI Character Set</span></span>
<span data-ttu-id="4206b-103">使用及參與字元或抑音符號 （'） 時，指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="4206b-103">When using the Ñ character or a grave accent (\`), specify the following:</span></span>  


|                                                                   |                                  <span data-ttu-id="4206b-104">字元集</span><span class="sxs-lookup"><span data-stu-id="4206b-104">Character Set</span></span>                                   |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------|
|             <span data-ttu-id="4206b-105">只有在 EDI 文件及參與字元</span><span class="sxs-lookup"><span data-stu-id="4206b-105">Only the Ñ character in the EDI document</span></span>              |                            <span data-ttu-id="4206b-106">使用擴充的字元集</span><span class="sxs-lookup"><span data-stu-id="4206b-106">Use Extended Character Set</span></span>                            |
|           <span data-ttu-id="4206b-107">只有抑音符號 (\`) 中的 EDI 文件</span><span class="sxs-lookup"><span data-stu-id="4206b-107">Only a grave accent (\`) in the EDI document</span></span>            |                              <span data-ttu-id="4206b-108">使用 UTF8 字元集</span><span class="sxs-lookup"><span data-stu-id="4206b-108">Use UTF8 Character Set</span></span>                              |
| <span data-ttu-id="4206b-109">及參與字元**並**抑音符號 (\`) 相同的文件中：</span><span class="sxs-lookup"><span data-stu-id="4206b-109">The Ñ character **and** a grave accent (\`) in the same document:</span></span> | <span data-ttu-id="4206b-110">-輸入文件必須具有 UTF8 編碼方式</span><span class="sxs-lookup"><span data-stu-id="4206b-110">-   The inbound document must have UTF8 encoding</span></span><br /><span data-ttu-id="4206b-111">-使用 UTF8 字元集</span><span class="sxs-lookup"><span data-stu-id="4206b-111">-   Use UTF8 Character Set</span></span> |

 <span data-ttu-id="4206b-112">下列連結提供者更多有關 EDI 字元集：</span><span class="sxs-lookup"><span data-stu-id="4206b-112">The following links provider more information on EDI Character Sets:</span></span>  

 [<span data-ttu-id="4206b-113">EDI 字元集</span><span class="sxs-lookup"><span data-stu-id="4206b-113">EDI Character Sets</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=271249)  

 [<span data-ttu-id="4206b-114">EDI 字元集支援</span><span class="sxs-lookup"><span data-stu-id="4206b-114">EDI Character Set Support</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=271250)