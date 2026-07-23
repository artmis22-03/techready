<!-- SideDock.svelte -->
<script lang="ts">
	import MailIcon from "@lucide/svelte/icons/mail";
	import HomeIcon from "@lucide/svelte/icons/house";
	import PencilIcon from "@lucide/svelte/icons/pencil";

	import { Separator } from "$lib/components/ui/separator";
	import * as Tooltip from "$lib/components/ui/tooltip/index.js";
	import { Button } from "$lib/components/ui/button";
	import { cn } from "$lib/utils";

	const DATA = {
		navbar: [
			{ href: "/", icon: HomeIcon, label: "Home" },
			{ href: "/about_Amarnath", icon: PencilIcon, label: "About Amarnath" },
		],
		contact: {
			social: {
				LinkedIn: { name: "LinkedIn", url: "#", icon: linkedInLogo },
			},
		},
	};
</script>

<!--
  Fixed vertical dock — pinned to the right edge of the viewport.
  Stays in place regardless of scroll position (position: fixed),
  vertically centered, sitting just inside the scrollbar.
-->
<div
	class="fixed top-1/2 right-3 z-50 hidden -translate-y-1/2 flex-col items-center gap-1
		rounded-full border bg-sky-100 p-2 shadow-lg backdrop-blur
		transition-all duration-300 hover:shadow-xl md:right-4 md:flex
		dark:bg-black/60"
>
	<Tooltip.Provider>
		{#each DATA.navbar as item}
			<Tooltip.Root>
				<Tooltip.Trigger>
					<Button
						href={item.href}
						aria-label={item.label}
						variant="ghost"
						size="icon"
						class={cn("size-11 rounded-full transition-transform hover:scale-110")}
					>
						<item.icon class="size-4" />
					</Button>
				</Tooltip.Trigger>
				<Tooltip.Content side="left">
					<p>{item.label}</p>
				</Tooltip.Content>
			</Tooltip.Root>
		{/each}

		<Separator class="w-6 bg-black" />

		{#each Object.entries(DATA.contact.social) as [name, social]}
			{@const socialIcon = social.icon}
			<Tooltip.Root>
				<Tooltip.Trigger>
					<Button
						href={social.url}
						aria-label={social.name}
						variant="ghost"
						size="icon"
						class={cn("size-11 rounded-full transition-transform hover:scale-110")}
					>
						{@render socialIcon()}
					</Button>
				</Tooltip.Trigger>
				<Tooltip.Content side="left">
					<p>{name}</p>
				</Tooltip.Content>
			</Tooltip.Root>
		{/each}
	</Tooltip.Provider>
</div>



{#snippet linkedInLogo()}
	<svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" class="size-4">
		<title>LinkedIn</title>
		<path
			fill="currentColor"
			d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"
		/>
	</svg>
{/snippet}

