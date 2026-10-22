# Changelog

## [v0.2.2](https://github.com/runapi-ai/wan-mcp/releases/tag/v0.2.2) - 2026-10-22

### Fixed
- Upgrade @modelcontextprotocol/sdk to ^1.32.1 to address security advisories.


## [v0.2.1](https://github.com/runapi-ai/wan-mcp/releases/tag/v0.2.1) - 2026-10-15

### Changed
- Wan 2.7 Image text-to-image accepts 1k or 2k; 4k remains available on Wan 2.7 Image Pro.


## [v0.2.0](https://github.com/runapi-ai/wan-mcp/releases/tag/v0.2.0) - 2026-09-30

### Changed
- Send tool arguments to the service without local model, enum, range, required-field, or cross-field validation. Tool descriptions still list declared types and known values.
  Migration: Invalid arguments now return the service's error, including its message, instead of a local tool-input rejection.
- Reject multi_shots on the models that do not support it: wan-2.2-a14b turbo, wan-2.5, and the wan-2.7 text, reference, image, and edit models.
  Migration: Send multi_shots only to a model that lists it.
- Limit duration_seconds to 5 or 10 and require output_resolution for wan-2.5 on text_to_video and image_to_video, and require audio for wan-2.6-flash-edit-video.
- Document the output_resolution defaults on animate, edit_video, image_to_video, speech_to_video, and text_to_video, and the 5-second duration_seconds default for wan-2.7-r2v.
- Depend on @runapi.ai/mcp-core 0.4.5 and send task creation and lookup to each tool's published route.


## [v0.1.9](https://github.com/runapi-ai/wan-mcp/releases/tag/v0.1.9) - 2026-07-31

### Changed
- Resolve MCP prices from the RunAPI Price Schedule API instead of embedded package data.


## [v0.1.8](https://github.com/runapi-ai/wan-mcp/releases/tag/v0.1.8) - 2026-07-28

### Fixed
- Use the complete Wan Flash image-to-video duration, resolution, and audio price schedule instead of coarse audio-only pricing.
- Expose the supported duration values and request defaults for Wan Flash image-to-video tools.


## [v0.1.7](https://github.com/runapi-ai/wan-mcp/releases/tag/v0.1.7) - 2026-07-20

### Fixed
- Reject `seed` for Wan 2.6 text-to-video and image-to-video tools using model-specific input rules.


## [v0.1.6](https://github.com/runapi-ai/wan-mcp/releases/tag/v0.1.6) - 2026-07-08

### Fixed
- Publish corrected MCP runtime metadata for the login release.

## [v0.1.5](https://github.com/runapi-ai/wan-mcp/releases/tag/v0.1.5) - 2026-07-08

### Changed
- Publish MCP login onboarding, optional API key metadata, and the updated core dependency.

## [v0.1.4](https://github.com/runapi-ai/wan-mcp/releases/tag/v0.1.4) - 2026-06-24

### Changed
- Publish wan-mcp v0.1.4.
- Pin the package to @runapi.ai/mcp-core v0.1.3.
- Refresh package and MCP Registry metadata for this release.

## [v0.1.3](https://github.com/runapi-ai/wan-mcp/releases/tag/v0.1.3) - 2026-06-24

### Changed
- Refresh public README metadata for the focused Wan MCP package.

### Fixed
- Correct the GitHub repository badge URL so package README badges render cleanly on npm and GitHub.

## [v0.1.2](https://github.com/runapi-ai/wan-mcp/releases/tag/v0.1.2) - 2026-06-24

### Changed
- Refresh the public README with focused install paths, model links, and agent prompt examples.
- Update npm and GitHub metadata for developer discovery.
- Keep server.json and packaged contract/pricing data aligned with the release artifact.

## [v0.1.1](https://github.com/runapi-ai/wan-mcp/releases/tag/v0.1.1) - 2026-06-24

### Changed
- Distinct per-line README, npm keywords/description, and GitHub topics for Wan so the package is discoverable on its own name and capabilities. No tool, schema, or behavior changes.

## [v0.1.0](https://github.com/runapi-ai/wan-mcp/releases/tag/v0.1.0) - 2026-06-24

### Added
- Initial release of the Wan MCP server: create tasks, poll their status, and check pricing for every Wan model with a single RunAPI API key.
