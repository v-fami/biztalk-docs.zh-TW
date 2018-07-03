---
title: SMTP 主控件屬性的限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [SMTP adapters], restrictions
- SMTP adapters, restrictions
ms.assetid: 6dbdb6dc-0062-4444-a4c8-6e2a7900f533
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2e8ef3800b67119bf9ffaffb4fd069064b640d1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985343"
---
# <a name="restrictions-on-the-smtp-host-property"></a><span data-ttu-id="17543-102">SMTP 主控件屬性限制</span><span class="sxs-lookup"><span data-stu-id="17543-102">Restrictions on the SMTP Host Property</span></span>
<span data-ttu-id="17543-103">SMTP 主控件屬性是一個字串，可指定 SMTP 配接器從 BizTalk 伺服器傳送訊息時將使用的 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="17543-103">The SMTP host property is a string that specifies the SMTP server that the SMTP adapter will use to send messages from the BizTalk server.</span></span>  
  
 <span data-ttu-id="17543-104">下列規則和限制適用於此屬性：</span><span class="sxs-lookup"><span data-stu-id="17543-104">The following rules and restrictions apply to this property:</span></span>  
  
- <span data-ttu-id="17543-105">此屬性必須設定在配接器處理常式層級、端點層級或同時設定。</span><span class="sxs-lookup"><span data-stu-id="17543-105">This property must be configured on the adapter handler level, on the endpoint level, or in both places.</span></span>  
  
- <span data-ttu-id="17543-106">SMTP 伺服器屬性不能包含下列字元: ' ~ ！</span><span class="sxs-lookup"><span data-stu-id="17543-106">The SMTP server property cannot contain the following characters: \` ~ !</span></span> <span data-ttu-id="17543-107">@ # $ ^ & \* ( ) = + [ ] { } \ &#124; ; : ' " , \< \> /, ?;</span><span class="sxs-lookup"><span data-stu-id="17543-107">@ # $ ^ & \* ( ) = + [ ] { } \ &#124; ; : ' " , \< \> /, ?;</span></span>  
  
- <span data-ttu-id="17543-108">SMTP 伺服器名稱的長度不可以超過 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="17543-108">The length of the SMTP server name must not exceed 256 characters.</span></span>  
  
  <span data-ttu-id="17543-109">SMTP 配接器永遠會使用先前提及的規則，在設計階段驗證 SMTP 主控件名稱。</span><span class="sxs-lookup"><span data-stu-id="17543-109">The SMTP adapter always validates the SMTP host name at design time by using the previously mentioned rules.</span></span> <span data-ttu-id="17543-110">此外，若訊息是透過動態連接埠以 SMTP 配接器來傳送，則 SMTP 配接器會在執行階段驗證 SMTP 主控件名稱。</span><span class="sxs-lookup"><span data-stu-id="17543-110">In addition, the SMTP adapter validates the SMTP host name at run time if a message is sent through a dynamic port with the SMTP adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17543-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17543-111">See Also</span></span>  
 [<span data-ttu-id="17543-112">設定 SMTP 配接器的限制</span><span class="sxs-lookup"><span data-stu-id="17543-112">Restrictions When Configuring the SMTP Adapter</span></span>](../core/restrictions-when-configuring-the-smtp-adapter.md)