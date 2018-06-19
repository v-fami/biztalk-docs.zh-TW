---
title: 自訂日期時間格式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5efbec4-3138-44d7-bc76-f9c21547e1d5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1496f1f506df06a4d5569c065cba3bf4f8cbdad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238470"
---
# <a name="custom-date-time-formats"></a><span data-ttu-id="8f476-102">自訂日期時間格式</span><span class="sxs-lookup"><span data-stu-id="8f476-102">Custom Date-Time Formats</span></span>

## <a name="overview"></a><span data-ttu-id="8f476-103">概觀</span><span class="sxs-lookup"><span data-stu-id="8f476-103">Overview</span></span>
<span data-ttu-id="8f476-104">您建立一般檔案結構描述使用的一般檔案格式，基於其舊有來源，會使用不符合 ISO 8601 格式的日期和時間格式。</span><span class="sxs-lookup"><span data-stu-id="8f476-104">Due to their legacy origins, the flat file formats for which you create flat file schemas are bound to use date and time formats that do not conform to ISO 8601 formats.</span></span> <span data-ttu-id="8f476-105">因此，您要建立一般檔案結構描述，而且您設定**資料型別**屬性**欄位項目**或**欄位屬性**節點的 XML 結構描述定義 （其中一個XSD) 語言基本資料型別**xs: datetime**， **xs: time**，或**xs: date**，您可以使用**自訂日期/時間格式**屬性來指定替代格式的日期或時間值。</span><span class="sxs-lookup"><span data-stu-id="8f476-105">Therefore, when you are creating a flat file schema and you set the **Data Type** property of a **Field Element** or **Field Attribute** node to one of the XML Schema definition (XSD) language primitive data types, **xs:dateTime**, **xs:time**, or **xs:date**, you can use the **Custom Date/Time Format** property to specify an alternative format for date or time values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f476-106">在訊息方塊中的儲存體截斷時間值中的**xs: datetime**和**xs: time**的毫秒以下項目。</span><span class="sxs-lookup"><span data-stu-id="8f476-106">Storage in the message box truncates time values in **xs:dateTime** and **xs:time** elements below the millisecond level.</span></span> <span data-ttu-id="8f476-107">轉換成 .NET日期/時間資料型別時，也可能發生類似的遺失有效位數的情況。</span><span class="sxs-lookup"><span data-stu-id="8f476-107">A similar loss of precision may occur when converting to .NET date/time data types.</span></span>  
  
 <span data-ttu-id="8f476-108">一般檔案解譯器會轉譯成其對等 XML 這類欄位時，將值格式化的**自訂日期/時間格式**屬性會用來允許轉換成它的 ISO 8601 相容的一般檔案日期/時間格式對等項目。</span><span class="sxs-lookup"><span data-stu-id="8f476-108">When the flat file disassembler translates such a field to its equivalent XML format, the value of the **Custom Date/Time Format** property will be used to allow the flat file date/time format to be converted to its ISO 8601 compliant equivalent.</span></span> <span data-ttu-id="8f476-109">同樣地，當一般檔案組合器會轉譯為相等的一般檔案的 ISO 8601 相容日期/時間值，指定的格式字串中**自訂日期/時間格式**屬性會用於建構適當的日期 /一般檔案中預期的時間格式。</span><span class="sxs-lookup"><span data-stu-id="8f476-109">Likewise, when the flat file assembler translates an ISO 8601 compliant date/time value to its flat file equivalent, the format string specified in the **Custom Date/Time Format** property will be used construct the appropriate date/time format expected in the flat file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f476-110">依照預設，與 XSD 日期和時間資料型別對應的值 (有數個) 都必須符合 ISO 8601 格式。</span><span class="sxs-lookup"><span data-stu-id="8f476-110">By default, values that correspond to XSD date and time data types, of which there are several, must conform to ISO 8601 formats.</span></span> <span data-ttu-id="8f476-111">簡單地說，日期以**YYYY MM DD**和小時會表示為**hh: mm:** 使用 24 小時制標記法。</span><span class="sxs-lookup"><span data-stu-id="8f476-111">In brief, dates are expressed as **YYYY-MM-DD** and hours are expressed as **hh:mm:ss** using 24-hour notation.</span></span> <span data-ttu-id="8f476-112">當一起出現時的日期和時間值會以"T"字元分隔： **YYYY:MM:DDThh:mm:ss**。</span><span class="sxs-lookup"><span data-stu-id="8f476-112">When they occur together, date and time values are separated by the "T" character: **YYYY:MM:DDThh:mm:ss**.</span></span>  
  
 <span data-ttu-id="8f476-113">您可以設定**自訂日期/時間格式**使用幾乎任何時間和日期的格式，除了儒屬性。</span><span class="sxs-lookup"><span data-stu-id="8f476-113">You can configure the **Custom Date/Time Format** property with almost any time and date format, except for Julian dates.</span></span> <span data-ttu-id="8f476-114">下拉式清單提供各種選擇，但您可以選擇自行輸入不同的格式。</span><span class="sxs-lookup"><span data-stu-id="8f476-114">The drop-down list provides various choices, but you can also type a different format of your choosing.</span></span> <span data-ttu-id="8f476-115">日期和時間格式使用 Common Language Runtime (CLR) **DateTime**設備。</span><span class="sxs-lookup"><span data-stu-id="8f476-115">The date and time formats use the Common Language Runtime (CLR) **DateTime** facilities.</span></span> <span data-ttu-id="8f476-116">唯一的例外是單一字元 d、m 或 M 開頭會自動加上百分比符號 (%)，以產生對應的 DateTime 值單一項目。</span><span class="sxs-lookup"><span data-stu-id="8f476-116">The exception is that a single character d, m, or M is automatically prepended with a percent sign (%) to yield the corresponding single element of the DateTime value.</span></span> <span data-ttu-id="8f476-117">自訂日期/時間格式允許的分隔符號為虛線 (-)、斜線及句號 (.)。</span><span class="sxs-lookup"><span data-stu-id="8f476-117">The allowable separators for custom date/time formats are dash (-), slash (/), and period (.).</span></span> <span data-ttu-id="8f476-118">如需有關**DateTime**格式，在 Visual Studio 文件集合中搜尋"Datetimeformatinfo"。</span><span class="sxs-lookup"><span data-stu-id="8f476-118">For more information about **DateTime** formats, search on "DateTimeFormatInfo" in the Visual Studio document collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f476-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f476-119">See Also</span></span>  
-  [<span data-ttu-id="8f476-120">欄位考量</span><span class="sxs-lookup"><span data-stu-id="8f476-120">Field Considerations</span></span>](../core/field-considerations.md)   
-  <span data-ttu-id="8f476-121">**資料型別 （所有結構描述的節點屬性）** 和**自訂日期時間格式 （一般檔案結構描述中的節點屬性）**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="8f476-121">**Data Type (Node Property of All Schemas)** and **Custom Date-Time Format (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>