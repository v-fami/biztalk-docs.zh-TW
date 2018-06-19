---
title: 疑難排解 Adapter2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcard characters, in send port properties
- troubleshooting adapter
- Get.xml
- send ports, using wildcards in properties
ms.assetid: e9e0408f-5a12-4f05-83a6-37dc519ae4c5
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 991278813d2183795239d1a75c08e474b2f8159a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279190"
---
# <a name="troubleshooting-the-adapter"></a><span data-ttu-id="18293-102">配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="18293-102">Troubleshooting the Adapter</span></span>
<span data-ttu-id="18293-103">本主題所含的資訊，可協助您辨識和解決在使用 Microsoft BizTalk Adapter for PeopleSoft Enterprise 時可能會遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="18293-103">This topic contains information to help you identify and resolve issues that you might experience while you are using Microsoft BizTalk Adapter for PeopleSoft Enterprise.</span></span>  
  
## <a name="cannot-use-wildcard-characters-in-send-port-properties"></a><span data-ttu-id="18293-104">無法在傳送埠屬性中使用萬用字元</span><span class="sxs-lookup"><span data-stu-id="18293-104">Cannot use wildcard characters in send port properties</span></span>  
 <span data-ttu-id="18293-105">BizTalk Adapter for PeopleSoft Enterprise 不支援在下列傳送埠屬性欄位中使用萬用字元：</span><span class="sxs-lookup"><span data-stu-id="18293-105">BizTalk Adapter for PeopleSoft Enterprise does not support using wildcard characters in the following send port property fields:</span></span>  
  
-   <span data-ttu-id="18293-106">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="18293-106">Username</span></span>  
  
-   <span data-ttu-id="18293-107">應用程式伺服器路徑</span><span class="sxs-lookup"><span data-stu-id="18293-107">App Server Path</span></span>  
  
-   <span data-ttu-id="18293-108">Java_Home</span><span class="sxs-lookup"><span data-stu-id="18293-108">Java_Home</span></span>  
  
-   <span data-ttu-id="18293-109">People JAR 檔案</span><span class="sxs-lookup"><span data-stu-id="18293-109">People JAR Files</span></span>  
  
## <a name="getxml-data-assigns-0001-01-01-value-for-null-dates"></a><span data-ttu-id="18293-110">Get.xml 資料針對 Null 日期指派 0001-01-01 值</span><span class="sxs-lookup"><span data-stu-id="18293-110">Get.xml data assigns 0001-01-01 value for null dates</span></span>  
 <span data-ttu-id="18293-111">Get.xml 不正確地針對 Null 日期指派 0001-01-01 值。</span><span class="sxs-lookup"><span data-stu-id="18293-111">Get.xml incorrectly assigns 0001-01-01 value for null dates.</span></span> <span data-ttu-id="18293-112">如果您想要以 null 取代 0001-01-01，您必須使用 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="18293-112">You must use the BizTalk Mapper tool if you want to replace the 0001-01-01 with null.</span></span>  
  
## <a name="creating-and-updating-properties-with-collections-fails"></a><span data-ttu-id="18293-113">建立和更新含有集合的屬性失敗</span><span class="sxs-lookup"><span data-stu-id="18293-113">Creating and updating properties with collections fails</span></span>  
 <span data-ttu-id="18293-114">配接器搭配 PeopleSoft 8.17.02 版使用時，配接器可以從 PeopleSoft 伺服器正確讀取資料。</span><span class="sxs-lookup"><span data-stu-id="18293-114">When using the Adapter with PeopleSoft version 8.17.02, the Adapter can read data from PeopleSoft server correctly.</span></span> <span data-ttu-id="18293-115">不過，建立和更新含有集合的屬性將會失敗。</span><span class="sxs-lookup"><span data-stu-id="18293-115">However, creating and updating fails for properties with collections.</span></span> <span data-ttu-id="18293-116">這是 PeopleSoft 的已知問題，可能會在 PeopleSoft 的後續版本中修正。</span><span class="sxs-lookup"><span data-stu-id="18293-116">This is a known PeopleSoft issue that may be fixed in a future release of PeopleSoft.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18293-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18293-117">See Also</span></span>  
 [<span data-ttu-id="18293-118">疑難排解 peoplesoft 問題</span><span class="sxs-lookup"><span data-stu-id="18293-118">Troubleshooting PeopleSoft</span></span>](../core/troubleshooting-peoplesoft.md)